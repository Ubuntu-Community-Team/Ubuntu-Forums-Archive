---
title: "After LAMP install"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by countcet on 2006-05-06
OK, I'm new to Linux and Ubuntu. I have successfully installed mysql and apache etc using apt-get but now I am just wondering... <stupid question>Where are those programs? </stupid question>

---

### Post by Sef on 2006-05-06
Apache is an open source http server.

Mysql is an open source data base.

---

### Post by countcet on 2006-05-06
Yes I understand... How do I start using them?

---

### Post by Randomskk on 2006-05-06
Go to:
[http://localhost](http://localhost)

You'll probably find that the Apache server is auto started, and PHP will have been added to it's config file.
Not sure where Apache keeps it's htdocs on Ubuntu, look in /var for a folder like "httpd", "htdocs" or "www" or somesuch.

If you find a folder with a load of index.htmls, you've got it.

From command line, in that directory, run this command:
echo "<?php php_info() ?>" > test.php

Then visit this:
[http://localhost/test.php](http://localhost/test.php)

If PHP is installed, that should show you the PHP information.

---

### Post by garner_nc on 2006-05-06
[www.mysql.com](www.mysql.com)

This is the best place to start. There is an extensive user manual on-line.
 
The mysql server starts automatically at boot. To access using a terminal type

mysql -u root

at a terminal prompt. Also, you need to set a password for the root mysql user, then you need to create an account for regular usage. See the manual.

    You might want to install PHP also. PHP is a scripting language used to create database driven web-sites.  There's a lot of PHP info on the web also.

All the Best,
Doug White

---

### Post by countcet on 2006-05-06
Thanks, THis should be enough to get me started.

---

### Post by harisund on 2006-05-06
Apache is a server, meaning it runs in the background. Here are a couple of things you could do, if you are familiar with the command line: 

First, execute 'sudo netstat -plant | grep LISTEN' and that will show you all open ports on your computers. You should see apache2 listed, and so also will mysql be listed. That means those 2 are running. 

To stop apache2 you should do 'sudo invoke-rc.d apache2 stop' and to start it 'sudo invoke-rc.d apache2 start' . For mysql just substitute 'apache2' in the above for 'mysql'

Next, by default the folder that apache2 serves is /var/www. The configuration for apache2 is in /etc/apache2. Mainly you might want to edit the /etc/apache2/apache2.conf file and change in that the USER and GROUP directives to match yours. If you feel bold have a look in /etc/apach2/sites-available/default. To enable apache modules, use 'sudo a2enmod'

Next, mysql is a service too, that's constantly running. A good GUI to use would be something called 'mysql-admin'. Install that and use it to connect to your mysql server. Remember, mysql by default needs to be logged in with the username of 'root' and no 'password' into the machine 'localhost' (same machine). This root has *nothing* to do with a root user or administrator on the computer. It's solely mysql's

If you had installed php4/5 correctly, apache should already be knowing it. Just type up a quick php file and place it on /var/www and open up your browser and visit [http://localhost](http://localhost). You should see the php file you created. Click that and it should work. 

If you are planning on connecting to mysql using php you will need to open /etc/php4/ .. something something (I don't recollect) but the file name is something.ini I think. Open that, and search for mysql. You will find a line with a semicolon in the beginning. Remove that semicolon. 

Finally restart your apache2 and mysql using the above given commands and everything should be working.

Cheers

---

