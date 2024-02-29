pipeline{
    agent any
    tools{
        maven 'loval_maven'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo"Archiving the artifacts"
                    archuveArtifacts artifacts: '**/target/*.war'
                }
            }

        }
        stage('Deploy to tomcat server'){
            steps{
               deploy adapters: [tomcat7(credentialsId: 'e9f86c1d-d162-474c-bc0f-ffdc53d9fe4e', path: '', url: 'https://3.108.221.41:8282/')], contextPath: null, war: '**/*.war'
            }

        }
    }
}