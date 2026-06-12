---
title: "Problem working Apache-PHP5-MySQL"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by ThePolemistis on 2007-05-16
Hi,

I installed apache, php5 and mySQL but the php does not display correctly even though the file is in /var/www/
Im using ubuntu 7.04 and want to set up the 3 as localhost
When I restart apache by using command

```
sudo /etc/init.d/apache2 restart
```

I get:

```
 * Forcing reload of web server (apache2)...                                    
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

Can anyone tell me how to install it correclty please??

---

### Post by chamberlain2006 on 2007-05-16
That error message is ok, it just means that you have not set a fully qualified hostname (like [www.google.com)](www.google.com)).  What is your problem with PHP though?

---

### Post by ThePolemistis on 2007-05-16
> **chamberlain2006 said:**
> That error message is ok, it just means that you have not set a fully qualified hostname (like [www.google.com)](www.google.com)).  What is your problem with PHP though?

I get this printed:

[HTML]
<head>
</head>
<body>

<?php
	phpinfo();
?>
</body>
[/HTML]

when i should be getting the page.
I put the file in /var/www/ (which i believe is default directory for apache)

---

### Post by chamberlain2006 on 2007-05-16
Have you installed the necessary packages for PHP?  You need libapache2-mod-php5, which resolves the dependencies.  Make sure you have that installed.

---

### Post by Cypher on 2007-05-16
To fix your ServerName thing
```

sudo vi /etc/apache2/apache2.conf

```
Find the "ServerRoot" line and add
```
ServerName localhost
```
below it.

With just that, you should be able to point the browser to "localhost" and get the directory listing showing apache2-default, when you click on that directory you should get "It Worked!". If all that is true, then you can create a index.php file in the apache2-default directory with
```

<?php phpinfo(); ?>

```

There is no need to encase this file within HTML tags and be sure to put a .php extention to the file.

---

### Post by ThePolemistis on 2007-05-16
> **chamberlain2006 said:**
> Have you installed the necessary packages for PHP?  You need libapache2-mod-php5, which resolves the dependencies.  Make sure you have that installed.

yup... i did install that 

> 
To fix your ServerName thing
Code:
sudo vi /etc/apache2/apache2.conf
Find the "ServerRoot" line and add
Code:
ServerName localhost
below it.

With just that, you should be able to point the browser to "localhost" and get the directory listing showing apache2-default, when you click on that directory you should get "It Worked!". If all that is true, then you can create a index.php file in the apache2-default directory with
Code:
<?php phpinfo(); ?>
There is no need to encase this file within HTML tags and be sure to put a .php extention to the file.



the file is called test.php in /var/www/ directory
I added the ServerName line under ServerRoot line but hasen't made a difference
And my apache is installed correctly, since I do get the It Works! text in the top left hand corner.

This is the address in the opera browser window for the php file:

file://localhost/var/www/test.php

Any other solutions, or configuration files u require to identify the problem??

---

### Post by annda on 2007-05-16
check you if you have php in /etc/apache2/mods-enabled

if you do, check the file php5.conf to see if it has this line:
AddType application/x-httpd-php .php .phtml .php3

---

### Post by chamberlain2006 on 2007-05-16
There's your problem.  Any files in the /var/www directory are in the root of the web server.  That means that /var/www/test.php = [http://localhost/test.php](http://localhost/test.php).

---

### Post by ThePolemistis on 2007-05-16
> **annda said:**
> check you if you have php in /etc/apache2/mods-enabled

if you do, check the file php5.conf to see if it has this line:
AddType application/x-httpd-php .php .phtml .php3

ok in my mods-enabled directory I do not  have php
I have these files:
```
alias.load          authz_groupfile.load  cgi.load  mime.load
auth_basic.load     authz_host.load       dir.conf  negotiation.load
authn_file.load     authz_user.load       dir.load  setenvif.load
authz_default.load  autoindex.load        env.load  status.load
```

so do u know what the problem is?

---

### Post by ThePolemistis on 2007-05-16
> **chamberlain2006 said:**
> There's your problem.  Any files in the /var/www directory are in the root of the web server.  That means that /var/www/test.php = [http://localhost/test.php](http://localhost/test.php).

actually... sorry.... i gave u the wrong address
I gave u file://localhost/var/www ... which is correct since in this case the root iis / i.e. localhost because its file://
when i do http:// my local host is /var/www

So do u know where the problem lies?

---

### Post by chamberlain2006 on 2007-05-16
If you are trying to dosplay the fle through file:///var/www/test.php, it won't work because it doesn't know how to display .php files.  That's why we have apache.  So if you want to show the file, you have to go to [http://localhost/test.php](http://localhost/test.php)

---

### Post by annda on 2007-05-16
make sure you have the libapache2-mod-php5 package installed, as mentioned by chamberlain2006. check synaptic for that. if you have installed it and restarted apache2 / rebooted and still have problems with php, please post back.

---

### Post by ThePolemistis on 2007-05-16
> **annda said:**
> make sure you have the libapache2-mod-php5 package installed, as mentioned by chamberlain2006. check synaptic for that. if you have installed it and restarted apache2 / rebooted and still have problems with php, please post back.


i can assure you I do have libapache2-mod-php5 installed. I also restarted apache several times as well as the computer.

I think apache is installed correctly,,, because i get the It Works! message. the phpinfo() script doesnt work so the problem maybe in php, but it is installed with the lib you listed above. 
Is there additional stuff that need to be configured after installed apache and php, like some conf files?


Do you know what could be the other reasons?

---

### Post by chamberlain2006 on 2007-05-16
No, the config files should have beeen installed automatically.  To make sure, do
```
ls /etc/apache2/mods-enabled | grep php
```
which should show something like php5.load php5.conf.  And you're sure you're running it through localhost/test.php?

---

### Post by ThePolemistis on 2007-05-16
> **chamberlain2006 said:**
> No, the config files should have beeen installed automatically.  To make sure, do
```
ls /etc/apache2/mods-enabled | grep php
```
which should show something like php5.load php5.conf.  And you're sure you're running it through localhost/test.php?

I dont get anything shown
yep im sure im running it from [http://localhost/test.php](http://localhost/test.php)

---

### Post by ThePolemistis on 2007-05-16
This is the contents of that folder ls (/etc/apache2/mods-enabled ) as stated earlire:

```
alias.load          authz_groupfile.load  cgi.load  mime.load
auth_basic.load     authz_host.load       dir.conf  negotiation.load
authn_file.load     authz_user.load       dir.load  setenvif.load
authz_default.load  autoindex.load        env.load  status.load
```

---

### Post by chamberlain2006 on 2007-05-16
You've got to enable the module.  Make sure that you have the php5.conf/php5.load files in the mods-available folder.  Then do a2enmod php5 to enable the module.  That is probably your problem.

---

### Post by ThePolemistis on 2007-05-16
> **chamberlain2006 said:**
> You've got to enable the module.  Make sure that you have the php5.conf/php5.load files in the mods-available folder.  Then do a2enmod php5 to enable the module.  That is probably your problem.

thanks ever so much... you have fixed my problem

im really happy.... now i can get on with my php work :)
I did it under windows... and it was much easier than this... but saying that.... on linux it doesnt use as much resources,,, and java works gr8 on linux... so i will stick to linux for a while XDXDXD

thanks again!!!

---

### Post by esoterica on 2007-05-16
That snippet of HTML code you gave is a problem as well the php stuff for the document declaration of your code needs to be at the very top of your page, not below the head portion. Since your just trying to run PHP info this is not what you want...

Wrong ```

<head>
</head>
<body>

<?php
	phpinfo();
?>
</body>

```

All your text file should look like to make this PHP file is the following...

```

<?php phpinfo() ?>

```

Nothing more, nothing less, save that as whatever.php and then run it to pull up all the stats on your PHP install. Then when running your own PHP scripts you have to make sure your document declaration is set for php and it has to be the very first line in your code.

---

### Post by nickruiz on 2007-05-16
I hope you don't mind me regurgitating ThePolemistis's problem. I have the same problem. I followed the steps outlined in this thread. I installed php5 and libapache2-mod-php5 and then checked my mods-enabled folder. Sure enough, the php5.conf and php5.load files were not there, so I used the a2enmod php5 command, which moved the two files from the mods-available to the mods-enabled folder.

In summary, I used the following commands:
```

root@UberUbuntu:~# a2enmod php5
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.
root@UberUbuntu:~# /etc/init.d/apache2 force-reload
root@UberUbuntu:~# /etc/init.d/apache2 stop
 * Stopping web server (apache2)...                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
                                                                         [ OK ]
root@UberUbuntu:~# /etc/init.d/apache2 start
root@UberUbuntu:~#

```

Unfortunately, I still cannot access my test.php file, though I can access the placeholder page. Any ideas?

---

### Post by Arghesis on 2007-05-19
Hi, I'm having a different problem with Apache2, PHP5 and MySQL.

I changed the apache2.conf file ServerRoot "home/pavel/www"
But it's not working. It shows another page with two links : 
1. apache2-default (which sais It works ! when I click it)
2.phpmyadmin

I installed phpmyadmin, but when I try to enter it, it requires a username and password. I searched the net about this problem but couldn't fixed it.

Please help me. I'm new to Linux and I need Apache, PHP and MySQL.

Thanks

---

### Post by hyper_ch on 2007-05-19
when you install mysql it does not setup a root password... so logging in with phpmyadmin would be:

User:  root
Pass: <blank>

---

### Post by Arghesis on 2007-05-19
When I type that it says

Error
 #2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)

and at the login it sais
Username: user
Password: * * * *

---

### Post by nickruiz on 2007-05-19
> **nickruiz said:**
> I hope you don't mind me regurgitating ThePolemistis's problem. I have the same problem. I followed the steps outlined in this thread. I installed php5 and libapache2-mod-php5 and then checked my mods-enabled folder. Sure enough, the php5.conf and php5.load files were not there, so I used the a2enmod php5 command, which moved the two files from the mods-available to the mods-enabled folder.

In summary, I used the following commands:
```

root@UberUbuntu:~# a2enmod php5
Module php5 installed; run /etc/init.d/apache2 force-reload to enable.
root@UberUbuntu:~# /etc/init.d/apache2 force-reload
root@UberUbuntu:~# /etc/init.d/apache2 stop
 * Stopping web server (apache2)...                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
                                                                         [ OK ]
root@UberUbuntu:~# /etc/init.d/apache2 start
root@UberUbuntu:~#

```

Unfortunately, I still cannot access my test.php file, though I can access the placeholder page. Any ideas?

It turns out that my Apache2 installation had an issue with the SSL module, so I ran a2dismod ssl and the problem seemed to clear up. We'll see what happens when I try enabling SSL again....

---

