pipeline {
    agent any 
    stages {
        stage('Clone repo') { 
            steps {
	        	echo 'Cloning ...'
	        	sh "rm -rf /var/lib/jenkins/workspace/java-pipeline/java"
                sh "git clone https://github.com/pabloccna/java-pipeline.git"
            }
        }
        stage('Build') { 
            steps {
		        echo 'Building ...'
                sh "javac /var/lib/jenkins/workspace/test-pipe/java/HelloWorld.java"
            }
        }
        stage('Run') { 
            steps {
                echo 'Running ...'
	        	sh "cd /var/lib/jenkins/workspace/java-pipeline/java"
	        	sh "java HelloWorld"
            }
        stage('Slack notification ...') { 
            steps {
                echo 'Notificating ...'
	        	slackSend baseUrl: 'https://hooks.slack.com/services/', 
                channel '#testing-java-slack-jenkins', 
                color: 'good', 
                message: 'Welcome to jenkins via slack, via Git con un Pipeline en Jenkis',
                teamDomain: 'javahomecloud',
                tokenCrendentialId: '4cyFjkMh078RGXbVAxXibqfc'
            }
        }
    }
}
