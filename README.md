# wordpress--setup
# installation of wordpress
# install nginx

install nginx https://nginx.org/en/linux_packages.html?_ga=2.10112373.1127578163.1726983257-157896506.1715837457#Ubuntu

sudo systemctl start nginx 

# Install and Configure MySQL Database
# install mysql
sudo apt install mysql-server

sudo mysql

show databases;

create database Wordpress;

CREATE USER 'wordpress'@'localhost' IDENTIFIED BY 'hello';

GRANT ALL PRIVILEGES ON Wordpress.* TO 'wordpress'@'localhost';

FLUSH PRIVILEGES;

EXIT;

# Install PHP
 
sudo add-apt-repository ppa:ondrej/php

sudo apt update

sudo apt install php7.2-cli php7.2-fpm php7.2-mysql php7.2-json php7.2-opcache php7.2-mbstring php7.2-xml php7.2-gd php7.2-curl

php -v

# Install WordPress with Nginx

sudo mkdir -p /var/www/html/devops.com

sudo wget https://wordpress.org/latest.tar.gz

sudo tar xf latest.tar.gz

sudo mv wordpress/* /var/www/html/devops.com/

sudo chown -R www-data: /var/www/html/devops.com/

# to change ownership nginx
ps -aux | grep nginx

sudo vim /etc/nginx/nginx.conf

sudo nginx -t

sudo nginx -s reload

ps -aux | grep php

sudo vim conf.d/default.conf
# click on github link
https://github.com/rajagaurdevops/wordpress/blob/main/default.conf

sudo nginx -t

sudo nginx -s reload

sudo apt update

# certbot certificate

sudo apt install certbot python3-certbot-nginx

sudo certbot --nginx -d devopsworldconsultancy.comg