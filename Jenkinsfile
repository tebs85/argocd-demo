pipeline {
    agent any
    stages {

        stage('Build') {
            agent { dockerfile true }

            steps {
                echo 'Hi, ArgoCD. Starting to build the App.'
            }   
        }

        stage('Test') {
            steps {
                input('Do you want to proceed?')
                sh 'node --version'
            }
        }

        stage('Deploy') {
            parallel { 

                stage('Deploy start') {
                    steps {
                        echo "Start the deploy .."
                    } 
                }

                stage('Deploying now') {
                    agent {
                        docker { image 'node:14-alpine' }
                    }
                    
                    steps {
                        echo "Docker Created"
                    }
                }
            }
        }

        stage('Prod') {
            steps {
                echo "App is Prod Ready"
            }
        }

    }
}
