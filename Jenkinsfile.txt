pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build step (nothing to compile for static site)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying static site...'
                sh '''
                mkdir -p /tmp/site
                cp *.html *.css /tmp/site
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
    }
}
