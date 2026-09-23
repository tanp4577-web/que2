pipeline {
    agent any // Automatically runs on your local Jenkins node

    stages {
        stage('Checkout') {
            steps {
                // Clones your new que2 repository path explicitly
                git url: 'https://github.com/tanp4577-web/que2.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Calls python module explicitly to guarantee execution access
                bat '''
                python -m pip install --upgrade pip --quiet
                python -m pip install -r requirements.txt --quiet
                '''
            }
        }

        stage('Run Unit Tests') {
            steps {
                // Executes pytest via the python module runner with verbose formatting flag (-v)
                bat 'python -m pytest -v test_app.py'
            }
        }
    }

    post {
        success {
            echo '===================================='
            echo 'SUCCESS: All stages passed perfectly!'
            echo '===================================='
        }
        failure {
            echo '===================================='
            echo 'FAILURE: The build or tests failed!'
            echo '===================================='
        }
    }
}
