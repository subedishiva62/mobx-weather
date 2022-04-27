pipeline {
  agent any

  tools {
    nodejs "nodejs"
  }

  stages {

    stage('Pullcode ') {
      steps {
        git 'https://github.com/subedishiva62/mobx-weather.git'
      }
    }

    stage('Build') {
      steps {
        sh 'npm install'
         sh 'npm run build'
      }
    }
    
    stage('compress') {
      steps {
        sh 'cd /var/lib/jenkins/workspace/weather'
        sh "tar cvzf buid-${currentBuild.number}.tar.gz build"
         
      }
    }


stage('deploy a code ') {
     steps {
      sh 'cd /var/lib/jenkins/workspace/weather'
       //sh 'echo checking checking'
      
      // sh "scp -P 22044  buid-${currentBuild.number}.tar.gz niraj@110.44.119.237:"
      sh "scp buid-${currentBuild.number}.tar.gz ubuntu@172.31.12.68:"
       //sh "ssh -p 22044 niraj@110.44.119.237 tar -xvf buid-${currentBuild.number}.tar.gz --directory  /usr/share/nginx/html/"
       sh "ssh  ubuntu@172.31.12.68 tar -xvf buid-${currentBuild.number}.tar.gz --directory  /usr/share/nginx/html/"

      }
    }
  }
}

