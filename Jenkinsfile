pipeline {
  environment {
    dockerimagename = "poorvashay/nodeapp"
    dockerImage = ""
  }
  
  agent any

  stages {

//     stage('Checkout Source') {
//       steps {
//         git 'https://github.com/poorvashay/kubernetes_Jenkins_deployment.git'
//       }
//     }
        
    stage('Build Container') {
      steps {
        echo 'Building Container..'
                script {
                    def dockerHome = tool 'MyDocker'
                    env.PATH = "${dockerHome}/bin:${env.PATH}"
                }
      }
    }

    stage('Build image') {
      steps{
        script {
          dockerImage = docker.build dockerimagename
        }
      }
    }
      
          stage('Build B') {
             steps {
                 build job: "Sonar_Project", wait: true
                    }
                }

//     stage('Pushing Image') {
//       environment {
//                registryCredential = 'dockerhubcred'
//            }
//       steps{
//         script {
//           docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
//           dockerImage.push("${env.BUILD_NUMBER}")            
//           dockerImage.push("latest")        
//           }
//         }
//       }
//     }

//     stage('Deploying App to Kubernetes') {
//       steps {
//         script {
//           kubernetesDeploy(configs: "deploymentservice.yml", kubeconfigId: "kubernetes")
//         }
//       }
//     }

  }

}
