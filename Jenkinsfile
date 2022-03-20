pipeline {
    agent any

//    options {
//      timeout(time: 5, unit: 'MINUTES') 
//    }
    stages {
        stage('Git Clone') {
            steps {
               git branch: 'main', url: 'https://github.com/nodejs211/hello-world'
            }
        }
        
        stage('build docker image') {
            steps {
                sh 'sudo docker build . -t nodejs'
                sh 'sudo docker run -d -p 8083:3000 nodejs'
                sh 'sudo docker image tag nodejs:latest kapilch/nodejs:latest'
                sh 'sudo docker push kapilch/nodejs:latest'
            }
        }
    }
}
