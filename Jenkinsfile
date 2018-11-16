pipeline {
	agent any

    	stages {
		stage('Build') {
			steps{
				bat 'call "cmd /b /c start C:\\Contrast\\Jenkins\\WebGoat7\\startwebgoat.cmd"'
				sleep 30
			}
		}
        	stage('Selenium Tests') {
			steps{
            			bat 'java -Dwebdriver.gecko.driver=C:\\Contrast\\Selenium\\geckodriver\\geckodriver.exe -jar C:\\Contrast\\Selenium\\selenium-html-runner-3.13.0.jar -htmlSuite *firefox http://localhost:8080/WebGoat/start.mvc C:\\Contrast\\Selenium\\Jenkins\\WebGoatTestSuite.html C:\\Contrast\\Selenium\\Selenium\\myresults.htm'
        		}
		} 
        	stage('Contrast Verification') {
			steps{
            			contrastVerification profile: 'Demo Profile', applicationName: 'WebGoat7_Jenkins_Selenium-Master', count: 0, severity: 'High'
        		}
		}
        }
}
