pipeline {
  agent {
    node 'master'
  }
  stages {
    stage('Build result') {
      steps {
        sh 'sudo docker build -t sanjeebbac/result ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'sudo docker build -t sanjeebbac/vote ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'sudo docker build -t sanjeebbac/worker ./worker'
      }
    }
    stage('Push result image') {
      when {
        branch 'master'
      }
      steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'sudo docker push sanjeebbac/result'
        }
      }
    }
    stage('Push vote image') {
      when {
        branch 'master'
      }
      steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'sudo docker push sanjeebbac/vote'
        }
      }
    }
    stage('Push worker image') {
      when {
        branch 'master'
      }
      steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'sudo docker push sanjeebbac/worker'
        }
      }
    }
  }
}
