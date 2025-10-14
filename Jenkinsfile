pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo '📥 Checking out the same repo using checkout scm...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo '🏗️ Running Maven build...'
                sh 'mvn -B clean package'
            }
        }

        stage('Archive Artifact') {
            steps {
                echo '📦 Archiving WAR file...'
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
    }

    post {
        success {
            echo '✅ Build Successful!'
        }
        failure {
            echo '❌ Build Failed!'
        }
    }
}
