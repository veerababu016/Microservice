pipeline {
    agent any  

    stages {
        stage('Deploy to kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-sc', namespace: 'webapps', serverUrl: 'https://DE9CD67283FD4A94ADF87D8E805A1B76.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  
                }
            }
        }
        
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-sc', namespace: 'webapps', serverUrl: 'https://DE9CD67283FD4A94ADF87D8E805A1B76.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
