pipeline {
    agent any

    tools {
        maven 'maven'   // change to your configured name
        jdk 'jdk'       // change to your configured name
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ullasg415-cmd/DevJenkins.git'
            }
        }

        stage('Build & Test') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Run Application') {
            steps {
                // Run in background so pipeline doesn't hang
                sh 'nohup java -jar target/MyMavenApp-1.0-SNAPSHOT.jar &'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
