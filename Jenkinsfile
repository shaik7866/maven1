node('master') 
{
    stage('continousdownload')
    {
        git 'https://github.com/shaik7866/maven1.git'
    }
    stage('continousbuild')
    {
        sh 'mvn package'
    }
     stage('continousdeploy')
    {
       sh '''scp /home/ubuntu/.jenkins/workspace/declarative/webapp/target/webapp.war ubuntu@172.31.23.216:/var/lib/tomcat8/webapps/testing.war'''
    }
    stage('continoustesting')
    {
        git 'https://github.com/shaik7866/Test1.git'
        
        sh 'java -jar /home/ubuntu/.jenkins/workspace/declarative/testing.jar'
        
    }
    stage('continousdelivery')
    {
        sh '''scp /home/ubuntu/.jenkins/workspace/declarative/webapp/target/webapp.war ubuntu@172.31.0.111:/var/lib/tomcat8/webapps/proding.war'''
    }
}
