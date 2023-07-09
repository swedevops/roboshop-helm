pipeline {

 agent any

 parameters{
   string(name: 'component', defaultValue: '', description: 'App Component Name')
   string(name: 'app_version', defaultValue: '', description: 'App Version')

 }

 stages {

   stage('Clone App Repo') {
     steps {
       dir('APP') {
           git branch: 'main', url: 'https://github.com/swedevops/${component}'
       }
      }

    }

   stage('Helm Deploy') {
   steps {

     sh 'helm upgrade -i ${component} . -f APP/value.yaml --set app_version=${app_version}'

     }
  }

 }

}