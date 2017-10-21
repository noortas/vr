#!groovy

node {
  try {
    def nodejsVersion = '8.1.3'


    stage('Checkout') { // for display purposes
      echo 'Downloading code from BitBucket'
      // Checkout git repo
      checkout scm
      // Get nodejs tool.
      tool name: "${nodejsVersion}", type: 'nodejs'
    }
    stage('Prepare') {
      nodejs(nodeJSInstallationName: nodejsVersion) {
       echo 'npm working'
      }
    }
    stage('Test') {
      echo 'Testing ...'
    }
    stage('Deploy-Dev') {
      nodejs(nodeJSInstallationName: nodejsVersion) {
        echo 'Deploying to dev with gradle- environment'
      }

    }
    stage('Integration-Test') {
      echo 'Integration tests are done'
    }
    stage('Deploy-Prod') {
      echo "Deploying to prod - environment"
    }

    stage('docker') {

      docker.image('ruby:2.3.1').inside {
      }


    }

  } finally {
    deleteDir()
  }
}
