pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }

        stage('Test') {
            steps {
                sh 'test -f build/index.html'
            }
        } // <--- 'Test' 스테이지를 닫는 중괄호
    } // <--- 모든 stages를 닫는 중괄호
} // <--- 전체 pipeline을 닫는 중괄호