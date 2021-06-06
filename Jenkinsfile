pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'f007aea6-fb34-45bd-928d-178f6aa6d091', url: 'git@github.com:xiaoming199411/web_demo.git']]])
                echo "pull code complete."
            }
        }
        stage('build project') {
            steps {
                sh 'mvn clean package'
                echo "build project complete."
            }
        }
        stage('publish project') {
            steps {
                deploy adapters: [tomcat7(credentialsId: '2f1f0892-f04a-4b03-b113-6999688b1677', path: '', url: 'http://192.168.240.132:8080/')], contextPath: null, war: 'target/*.war'
                echo "publish project complete."
            }
        }
    }
}

