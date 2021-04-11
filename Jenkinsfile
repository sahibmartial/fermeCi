/* import shared library */
@Library('jenkins-shared-library')_

 /*sectiondev*/
pipeline {
    agent none
   environment {
        CI = 'true'
   } 
   stages {
       /* stage('Check go syntax') {
            agent { docker { image 'eeacms/golint' } }
            steps {
                sh 'golint  \${WORKSPACE}/main.go'
            }
        }*/
        

        stage('Check docker-compose syntax') {
            agent { docker { image 'docker/compose' } }
            steps {
                sh 'docker-compose -f \${WORKSPACE}/docker-compose.yml config'
            }
        }
        /*           
        stage('Check Dockerfile syntax') {
            agent { docker { image 'hadolint/hadolint' } }
            steps {
                sh 'hadolint \${WORKSPACE}/Dockerfile'
            }
        } */          
       
   } 
   post {
    always {
       script {
         /* Use slackNotifier.groovy from shared library and provide current build result as parameter */
         clean
         slackNotifier currentBuild.result
        }
    }
    }      
 }
