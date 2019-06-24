pipeline {
    agent any
    stages {
		stage('Dummy Build') {
            steps {
                sh "echo 'Hello world!'"
            }
        }
		stage('Pull request scan') {
            when {
                // Only for master
                expression { env.BRANCH_NAME.startsWith('PR-') }
            }
            steps {               
				sh "/home/mukhersi/softwares/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner -Dsonar.analysis.mode=preview -Dsonar.github.oauth=7a444fa2da4492286420993cedc80b8d8c2ebc1a -Dsonar.github.repository=sidd9433/machine_learning_examples  -Dsonar.github.pullRequest=1 -X"
            }
        }
        stage('Sonar Scan') {
            when {
                // Only for master
                expression { env.BRANCH_NAME == 'master' }
            }
            steps {
                sh '/home/mukhersi/softwares/sonar-scanner-3.3.0.1492-linux/bin/sonar-scanner'
            }
        }
		stage('Dummy Prepare for release') {
			when {
                // Only for master
                expression { env.BRANCH_NAME == 'master' }
            }
            steps {
                sh "echo 'ummy Prepare for release!'"
            }
        }
		stage('Dummy Deploy') {
			when {
                // Only for master
                expression { env.BRANCH_NAME == 'master' }
            }
            steps {
                sh "echo 'Dummy Deploy!'"
            }
        }
    }
}
