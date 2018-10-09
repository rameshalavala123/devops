#!groovy

node {
    currentBuild.result = "SUCCESS"

    try {

       stage('Checkout'){

          checkout scm
       }

       stage('Compiling'){

          sh 'mvn clean install'
       }
	   
      stage('Sonar') {
                    //add stage sonar
                    sh 'mvn sonar:sonar'
                }
	    
	stage('Checkstyle') {
                    sh 'mvn checkstyle:checkstyle'
                }

               stage('PMD') {
                    sh 'mvn pmd:check'
                }
      /* stage('mail'){

         mail body: 'project build successful',
                     from: 'ramesh.alavala@gmail.com',
                     replyTo: 'ramesh.alavala@capgemini.com',
                     subject: 'project build successful',
                     to: 'ramesh.alavala@capgemini.com'
       }*/
	    
	    

    }
    catch (err) {

        currentBuild.result = "FAILURE"

           /* mail body: "project build error is here: ${env.BUILD_URL}" ,
            from: 'ramesh.alavala@gmail.com',
            replyTo: 'ramesh.alavala@capgemini.com',
            subject: 'project build failed',
            to: 'ramesh.a@capgemini.com’
            */
        throw err
    }
}

