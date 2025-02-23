pipeline {
    agent any

    tools{
        maven "maven"
    }

    stages {
        stage("Checkout code") {
            steps {
               checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/shivsundarbankar/jenkins-demo.git']])
            }
        }

        stage("Build scan"){
            steps{
                script{
                    sh 'mvn clean install -P production'
                }
            }
        }

        stage("Deploy to sever"){
            steps{
                deploy adapters: [tomcat9(credentialsId: '387deb94-efe3-49e2-b68a-6e0946cd54f8', path: '', url: 'http://localhost:9596/')], contextPath: 'testApp', war: '**/*.war'
            }
        }
    }
}

//checkout
//Build
//deploy
//email