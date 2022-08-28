def obj
pipeline{
    
    agent any
    environment{
        java_version = "1.2.3"
    }
    parameters{
        
        choice(name: 'version', choices: ['1','2','3'], description: 'choices')
    }
    stages{
        
        stage('build') {
            when{
                expression{
                    JOB_NAME == "pipeline_script"
                }
            }
            
            steps{
                echo 'build'
                script {
                obj=load "script.groovy"
                }
            }
        }
        stage('test') {
            when{
                expression{
                    params.version == '3'
                    
                    
                }
            }
            steps{
                echo 'test'
                echo " java version is ${java_version}"
                script {
                    obj.test()
                }
            }
        }
        stage('deploy') {
            
            steps{
                echo 'test'
            }
        }
    }
    post{
        
        always{
            echo 'post always'
        }
        success{
            echo 'sucess post check'
        }
        failure{
            echo 'failure post check'
        }
    }
    
}
