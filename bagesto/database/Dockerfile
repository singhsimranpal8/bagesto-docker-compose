FROM ubuntu:20.04
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update
RUN apt-get install -y mysql-server
RUN usermod -d /var/lib/mysql/ mysql
ENV user=root password=NewPassword
RUN sed -i 's/127.0.0.1/0.0.0.0/'  /etc/mysql/mysql.conf.d/mysqld.cnf && service mysql restart 
RUN /etc/init.d/mysql start && mysql -u$user -p$password -e "ALTER USER 'root'@'localhost' IDENTIFIED BY 'NewPassword';" && mysql -u$user -p$password -e "create database bagesto;" && mysql -u$user -p$password -e "CREATE USER 'testuser'@'%' IDENTIFIED WITH mysql_native_password BY 'webkul@123';" &&  mysql -u$user -p$password -e "GRANT ALL ON *.* TO 'testuser'@'%';"
EXPOSE 3306
CMD ["mysqld"]

