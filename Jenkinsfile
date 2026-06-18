pipeline 
{
agent any
environment {
LANG='en_US.UTF-8'
LC_ALL='en.US.UTF-8'
}
tools
{
maven 'Maven"
}
stages
{
stage ('checkout') {
steps {
git branch:'master' url:'https://github.com/vaishnavim1121/ansible.git'
}
stage ('build'){
steps {
sh 'mvn clean package'
}
}
stage ('archive'){
steps {
archiveArtifacts artifacts:'/target/*.war' fingerprint:true
}
}
stage ('deploy') {
steps {
sh 'mvn clean package'
sh ' ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
}
}
}
