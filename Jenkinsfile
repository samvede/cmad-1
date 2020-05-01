pipeline { 
agent any 
tools{ 
maven 'Maven 3.6.1' 
} 
stages{ 
stage("build"){ 
steps{ 
echo 'Compiling users app..' 
dir('java/cmad-1'){ 
sh 'mvn compile' 
} 
} 
} 
stage("test"){ 
steps{ 
echo 'Running Unit Tets on users app..' 
dir('java/cmad-1'){ 
sh 'mvn clean test' 
} 
} 
} 
stage("package"){ 
steps{ 
echo 'Packaging users app' 
dir('java/cmad-1'){ 
sh 'mvn package -DskipTests' 
archiveArtifacts artifacts: 'java/cmad-1/target/*.jar', 
fingerprint: true 
} 
} 
} 
} 
post{ 
always{ 
echo 'Building multibranch pipeline for users is completed..' 
} 
} 
