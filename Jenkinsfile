pipeline {
    agent {
        label 'slave1'
    }

    stages {
        stage('git clone') {
            steps {
                echo 'clone code from scm'
				git branch: 'main', url: 'https://github.com/rajeshgattu96/mindcircuit16d.git'
            }
        }
		
        stage('Build') {
            steps {
                echo 'build the artifact'
				sh 'maven clean install'
            }
        }

        stage('deploy') {
            steps {
                echo 'deploying to tomcat'
				deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://ec2-13-235-31-187.ap-south-1.compute.amazonaws.com:8080/')], contextPath: 'facebook', war: '**/*.war'
				
            }
        }
		
    }
}
