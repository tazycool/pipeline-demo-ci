node {

  stage ('Checkout') {
    checkout scm
  }

  stage ('Terraform Plan') {
    echo 'terraform plan -no-color -out=create.tfplan'
  }

  // Optional wait for approval
  input 'Deploy stack?'

  stage ('Terraform Apply') {
    echo 'Run terraform apply -no-color create.tfplan'
  }

  stage ('Post Run Tests') {
    echo "Insert your infrastructure test of choice and/or application validation here."
    sleep 2
    echo 'Runterraform show'
  }

  stage ('Notification') {
    mail from: "jenkins@mycompany.com",
         to: "devopsteam@mycompany.com",
         subject: "Terraform build complete",
         body: "Jenkins job ${env.JOB_NAME} - build ${env.BUILD_NUMBER} complete"
  }
}
