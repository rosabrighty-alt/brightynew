pipeline {
    agent any

    stages {
        stage('DB Connection') {
            steps {
                echo "Connecting to database..."
                // Simulate DB connection
                sh 'echo "DB connected ✅"'
            }
        }

        stage('Post-Connection Check') {
            steps {
                echo "Checking DB connection..."
                sh 'echo "DB connection OK ✅"'
            }
        }

        stage('Create Schema') {
            steps {
                echo "Creating schema..."
                sh 'echo "Schema created ✅" > schema_created.txt'
            }
        }

        stage('Populate Schema') {
            steps {
                echo "Populating schema..."
                sh '''
                echo "id,name,calories" > data.txt
                echo "1,Apple,52" >> data.txt
                echo "2,Banana,89" >> data.txt
                '''
            }
        }

        stage('Post-Build Notifications') {
            steps {
                echo "Pipeline finished successfully ✅"
            }
        }
    }

    post {
        always {
            echo "Cleaning up workspace..."
            sh 'rm -f schema_created.txt data.txt || true'
        }
        success {
            echo "Build succeeded ✅"
        }
        failure {
            echo "Build failed ❌"
        }
    }
}
