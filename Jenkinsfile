pipeline{

    agent any

    stages {

        stage ('Compile Stage') {

            steps {

                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn clean install'

                }

            }
        }
    stage ('Test Stage') {

            steps {

                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn test'

                }

            }
        }


        stage ('Cucumber Reports') {

            steps {
                cucumber buildStatus: "UNSTABLE",
                    fileIncludePattern: "**/cucumber.json",
                    jsonReportDirectory: 'target'

            }

        }
        stage ('Slack notification') {
                 slackSend channel: 'rivet-jenkins', 
                  color: 'red', 
                   iconEmoji: '', 
                    message: 'Slack', 
                     teamDomain: 'kaay', 
                     tokenCredentialId: 'Jenkins-slack', 
                     username: 'mahesh'
        }
    }

}
