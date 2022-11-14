pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=docker('dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git  'https://github.com/sukhanyam3/node-redis-mongo.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t sukhanya/node:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		
		stage('Push') {

			steps {
				sh 'docker push sukhanya/node:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
