pipeline{
    agent {
        label "ec2a"
    }
    stages{
       stage("git pull admin.conf"){
           step{
               git "https://github.com/prabal03/helm-jenkins-file.git" , branch "master"
               git "https://github.com/prabal03/helm-testing.git" , branch "master"
           }
       }
        stage("building helm"){
         step{
             sh "wget https://get.helm.sh/helm-v3.6.3-linux-amd64.tar.gz"
             sh "tar -xvzf helm-v3.6.3-linux-amd64.tar.gz"
             sh "mv linux-amd64/helm /usr/bin"
             sh "helm install app helm-testing --kubeconfig admin.conf"
         }
        }
    }
}