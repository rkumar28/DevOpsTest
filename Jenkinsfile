pipeline{
	agent any
	stages{
		stage('GIT-CHECKOUT'){
			steps{
				echo "Checking Out from Git Repo !!";
				git credentialsId: '9447d5bc-74df-4f62-8384-6c614730762b', url: 'https://github.com/rkumar28/DevOpsTest.git'
			}
		}
		stage('BUILD'){
			steps{
				echo "Building application!!";
				bat label: 'Application builing bat', script: 'Build.bat'
			}
		}
		stage('UNIT-TEST'){
			steps{
				echo "Running JUnit test!!";
				bat label: 'JUnit test execution bat', script: 'UnitTest.bat'
			}
		}
		stage('STATIC-CODE-ANALYSIS'){
			steps{
				echo "Verifying Quality Gates";
				bat label: 'Verify Quality Gate bat', script: 'Quality.bat'
			}
		}
		stage('DEPLOY-TO-INT'){
			steps{
				echo 'Deploying for stage deployment for more test';
				bat label: 'Deploy bat', script: 'Deploy.bat'
			}
		}
		stage('REGRESSION-TEST-EXECUTION'){
			steps{
				echo 'Executing Regression Test';
				//bat label: 'Regression test bat', script: 'Regression.bat'
			}
		}
		stage('DEPLOY-TO-PREPROD'){
			steps{
				echo 'Deploy to Pre Production Env';
				//bat label: 'Pre Production Deploy bat', script: 'DeployRelease.bat'
			}
		}
	}
	post{
		always{
			echo 'This will always run'
		}
		success{
			echo 'This will run only if succssful'
		}
		failure{
			echo 'This will run only if the run was marked as unstable..'
		}
		unstable{
			echo 'This will run only if the run was marked as unstable'
		}
		changed{
			echo 'This will run only if the state of the pipeline has changed.'
			echo 'For example, if the Pipeline was previously failing bit is now succssful..'
		}
	}
}
