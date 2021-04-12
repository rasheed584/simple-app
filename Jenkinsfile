pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
	stages{
		stage('Build'){
			steps{
				sh script: 'mvn clean packge'
			}
		}
		stage('Uploaded War to Nexus'){
			steps{
				nexusArtifactUploader artifacts: [
				[
					artifactId: 'simple-app',
					classifier: '', 
					file: 'target/simple-app/3.0.0.war',
					type: 'war'
				]
			], 
			credentialsId: 'nexus3', 
			groupId: 'in.javahome', 
			nexusUrl: '172.31.65.101:8081', 
			nexusVersion: 'nexus3',
			protocol: 'http', 
			repository: 'sample-App', 
			version: '3.0.0'
		}
	}
}
}
