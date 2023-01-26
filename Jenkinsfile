pipeline {
    agent {
        label {
            label 'built-in'
            customWorkspace '/mnt/jenkins-master'
        }
    }
    tools {
        maven 'mvn'
    }
    environment {
        url1 = "https://github.com/sayalip848/project.git"
        url2 = "https://github.com/sayalip848/project-repo.git -b ansible"
    }
    stages {
        stage ('git-checkout') {
            steps {
                sh "git clone ${url1}"
                sh "git clone ${url2}"
            }
        }
        stage ('build-project') {
            steps {
                sh "mvn clean install"
            }
        }
        stage ('deploy-dev') {
            sh "cd ansible && ansible-playbook mydevplaybook.yml"
        }
    }
}
