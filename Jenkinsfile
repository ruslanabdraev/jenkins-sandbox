pipeline {
  agent any
  stages {
        stage('restore') {
            steps {
                bat label: '', script: '<absolute_path>\\nuget.exe restore Solutionfile.sln'
            }
        }
        stage('build'){
            steps {
                bat "\"${tool 'MSBuild'}\" <relative_path>\Solutionfile.sln /t:Clean,Restore,Build"
            }
        }
    }
    post {
        always {mail to:"<email_address>",
            subject:"STATUS FOR PROJECT: ${currentBuild.fullDisplayName}",
            body: "RESULT: ${currentBuild.result}"
        }
    }
}
