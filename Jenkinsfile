pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
        stage('Merge to Staging') {
            when {
                branch 'development'
            }
            steps {
                script {
                    sh 'git checkout staging'
                    sh 'git merge development'
                    sh 'git push origin staging'
                }
            }
        }
        
        stage('Merge to Production') {
            when {
                branch 'staging'
            }
            steps {
                script {
                    sh 'git checkout production'
                    sh 'git merge staging'
                    sh 'git push origin production'
                }
            }
        }
    }
}

