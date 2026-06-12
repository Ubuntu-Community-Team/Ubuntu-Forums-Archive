---
title: "I want to install php4 on top of my existing php5"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by syn4k on 2008-03-18
I am rewriting code that was written in php4 but before I do this I need to fix some issues in the old release. I am getting fatal errors that indicate depreciated code is trying to run on my php5 box. This is because the code is php4. So I am guessing that the easiest way to fix this is to enable a toggle so I can code in both php4 and php5.

Here is my installation script that I use on every one of my php5 installations:
# Install LAMP
sudo apt-get -y install apache2 php5-mysql libapache2-mod-php5 mysql-server mysql-client-5.0 phpmyadmin
sudo echo 'ServerName localhost'>>/etc/apache2/httpd.conf
sudo echo 'Listen 8080'>>/etc/apache2/httpd.conf
sudo echo 'AddType application/x-httpd-php .php5'>>/etc/apache2/httpd.conf
sudo echo 'AddType application/x-httpd-php-source .php5s'>>/etc/apache2/httpd.conf
sudo echo ''>>/etc/apache2/httpd.conf
sudo echo ' DirectoryIndex index.html index.htm index.php index.php5'>>/etc/apache2/httpd.conf
sudo echo ''>>/etc/apache2/httpd.conf
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/nettekk
sudo mkdir /home/ray/public_html
sudo chmod -fR +rwxst /home/ray/public_html/
sudo chown -fR ray /home/ray/public_html/
sudo a2enmod php5
sudo a2dissite default && sudo a2ensite nettekk

What I need now is some tips on how I can take this setup and make the toggle possible. I don't want to destroy what I've got working already. I have already installed php4 from source.

Thanks.

---

### Post by spiderbatdad on 2008-03-18
the php4 module will not install in apache2 if the php5 module is enabled. You cannot have both php modules running on the same instance of apache2. Your "toggle" would need to uninstall libapache2-mod-php5 before installing php4 and vice versa, otherwise the php4 package will install libapache-mod-php4 not libapache2-mod-php4. 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

