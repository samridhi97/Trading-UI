pipeline {
   agent any
	stages {
      stage('SCM Checkout') {
         steps {
            git 'https://github.com/samridhi97/Trading-UI.git'
		}
	}
	stage('Build') {
		steps {
			sh '''
			npm install
			npm run build
			npm audit fix
			'''
		}
	}
	stage ('Deploy') {
		steps {
			sh '''
             cp -r $WORKSPACE/build /opt/apache-tomcat-9.0.35/webapps
             curl -u admin:admin http://3.21.56.4:8888/manager/reload?path=/build 
             '''
		}
	}
}
}
