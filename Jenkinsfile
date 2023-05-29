pipeline{
    agent any
     tools {
        maven 'Maven'
     }
    stages{
        stage("test"){
            steps{
                // mvn test
                sh "mvn test"
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("Deploy in test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails2', path: '', url: 'http://192.168.119.108:8080')], contextPath: '/app', war: '**/*.war'
                
            }
            
        }
        stage("Deploy in prod"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcatserverdetails2', path: '', url: 'http://192.168.119.131:8080')], contextPath: '/app', war: '**/*.war'
                
            }
            
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
