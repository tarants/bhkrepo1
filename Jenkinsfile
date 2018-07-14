pipeline{
	agent any
	stages {
		stage('checkout'){
		    steps
                {
                    script
                    {
	git'https://github.com/tarants/bhkrepo1.git'
                    }
                }
		}
		stage ('build') {
			steps {
				script {
					sh 'mvn clean package'
				}
			}
		}
stage ("Junit") {
            steps {
                script {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }


  post
    {
         success
        {
            script
            {
            
		    mail to: 'bhemanthk007@gmail.com',
                     subject: "Build + Condition Pass",
                     body: "Build got success check status @ ${env.BUILD_URL}"
                
            }
	}
        
          failure
	   {
		   script
		   {
                mail to: 'bhemanthk007@gmail.com',
                     subject: "Build fail + Condition Pass",
                     body: "Build got success check status @ ${env.BUILD_URL}"
                 
            }
        }
    }


