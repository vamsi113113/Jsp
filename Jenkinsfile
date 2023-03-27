node
{
def mavenHome =tool name: "Maven-3.9.1"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '5')), pipelineTriggers([githubPush()])])

stage('github webhook')
{
git branch: 'development', credentialsId: 'cd765832-ec7e-44c1-ae90-0c9f8f1e9223', url: 'https://github.com/vamsi113113/Jsp.git'
}
stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"
}
stage('email')
{
emailext body: '''github webhook

Regards,
Vamsidhar''', subject: 'github webhook', to: 'vamsidhar113@gmail.com'
}

}