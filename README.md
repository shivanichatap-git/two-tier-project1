# two-tier-project1
#Prerequisites
first you have to install docker and git if it is not installed then install it 
- Docker
- Git
# apt-get install docker.io
# apt-get install git
#cloning
then clone the repo you got repository 
# git clone

After the clonning go to that repository you got files and template folder
create docker image from that dockerfile
# docker build -t flaskapp .
Then, make sure that you created network
# docker network create twotier

attach both container with same network so the can communicate with each others

create container of mysql
# docker run -d --name mysql -v mysql-data:/var/lib/mysql --network=twotier -e MYSQL_DATABASE=mydb -e MYSQL_ROOT_PASSWORD=admin -p 3306:3306 mysql:5.7

create container of flask
# docker run -d --name flaskapp --network=twotier -e MYSQL_HOST=mysql -e MYSQL_USER=root -e MYSQL_PASSWORD=admin -e MYSQL_DB=mydb -p 5000:5000 flaskapp:latest

then copy ip of your instance and paste it in your browser to check 
# 35.173.235.192:5000
