pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.4/bin:$PATH"
}
    stages {
        stage("build"){
            steps {
                sh 'mvn clean deploy'
            }
        }

    stage('SonarQube analysis') {
    tools {
        jdk "java-11-openjdk" // the name you have given the JDK installation using the JDK manager (Global Tool Configuration)
    }
    
    environment {
      scannerHome = tool 'sonar-scanner-tell1619'
    }
    steps{
    withSonarQubeEnv('sonar-server-tell1619') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }
}
}