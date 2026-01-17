pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
              sh 'rm -rf build'
              sh 'mkdir build'
              sh 'cd build && cmake ..'
            }
        }
        stage('Test') {
            steps {
                sh 'cd ..'
                sh './build/casino_game'
                sh './build/test_game'
            }
        }
        stage('Deliver') {
            steps {
                sh 'tar -czf casino_game.tar.gz build/casino_game'
                archiveArtifacts artifacts: 'casino_game.tar.gz', fingerprint: true
            }
        }
    }
}
