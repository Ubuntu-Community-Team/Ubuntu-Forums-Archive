---
title: "installing php4 to apache2"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-11-27
root@r00t-server:/home/r00t# sudo apt-get install php4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache2-common apache2-mpm-prefork libapache2-mod-php4 libzzip-0-12
  php4-common
Suggested packages:
  apache2-doc php-pear
The following NEW packages will be installed:
  apache2-common apache2-mpm-prefork libapache2-mod-php4 libzzip-0-12 php4
  php4-common
0 upgraded, 6 newly installed, 0 to remove and 12 not upgraded.
2 not fully installed or removed.
Need to get 2774kB of archives.
After unpacking 7315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://na.archive.ubuntu.com](http://na.archive.ubuntu.com) edgy/main apache2-common 2.0.55-4ubuntu4 [807kB]
Get:2 [http://na.archive.ubuntu.com](http://na.archive.ubuntu.com) edgy/main apache2-mpm-prefork 2.0.55-4ubuntu4 [206kB]
Get:3 [http://na.archive.ubuntu.com](http://na.archive.ubuntu.com) edgy/universe libzzip-0-12 0.12.83-6 [34.0kB]
Get:4 [http://na.archive.ubuntu.com](http://na.archive.ubuntu.com) edgy/universe php4-common 4:4.4.2-1.1 [174kB]
Get:5 [http://na.archive.ubuntu.com](http://na.archive.ubuntu.com) edgy/universe libapache2-mod-php4 4:4.4.2-1.1 [1552kB]
Get:6 [http://na.archive.ubuntu.com](http://na.archive.ubuntu.com) edgy/universe php4 4:4.4.2-1.1 [1160B]                                                   
Fetched 2774kB in 17m25s (2653B/s)                                                                                          
Selecting previously deselected package apache2-common.
(Reading database ... 93942 files and directories currently installed.)
Unpacking apache2-common (from .../apache2-common_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package apache2-mpm-prefork.
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.0.55-4ubuntu4_i386.deb) ...
Selecting previously deselected package libzzip-0-12.
Unpacking libzzip-0-12 (from .../libzzip-0-12_0.12.83-6_i386.deb) ...
Selecting previously deselected package php4-common.
Unpacking php4-common (from .../php4-common_4%3a4.4.2-1.1_i386.deb) ...
Selecting previously deselected package libapache2-mod-php4.
Unpacking libapache2-mod-php4 (from .../libapache2-mod-php4_4%3a4.4.2-1.1_i386.deb) ...
Selecting previously deselected package php4.
Unpacking php4 (from .../php4_4%3a4.4.2-1.1_all.deb) ...
Setting up runit (1.6.0-1) ...
Adding SV inittab entry...
cp: omitting directory `/etc/inittab'
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Setting up ssh-krb5 (3.8.1p1-10build1) ...
/etc/ssh/sshd_config: line 73: Bad configuration option: AcceptEnv
/etc/ssh/sshd_config: terminating, 1 bad configuration options
invoke-rc.d: initscript ssh-krb5, action "restart" failed.
dpkg: error processing ssh-krb5 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up apache2-common (2.0.55-4ubuntu4) ...
Setting Apache2 not to start, as something else appears to be using Port 80. To allow apache2 to start, set NO_START to 0 in /etc/default/apache2. Apache2 has been set to listen on port 80 by default, so please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.

Setting up apache2-mpm-prefork (2.0.55-4ubuntu4) ...

Setting up libzzip-0-12 (0.12.83-6) ...

Setting up php4-common (4.4.2-1.1) ...
Setting up libapache2-mod-php4 (4.4.2-1.1) ...

Setting up php4 (4.4.2-1.1) ...

Errors were encountered while processing:
 runit
 ssh-krb5
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@r00t-server:/home/r00t# sudo /etc/init.d/apache2 restart
root@r00t-server:/home/r00t# gedit /var/www/testphp.php



i cant install anything .. please help me :'(
what is porblem ? please hurry up

---

### Post by shin on 2006-11-27
Try reinstalling/removing runit and ssh-krb5. These are the reason of erros, not php4 or apache.

---

### Post by az on 2006-11-27
> **pavel_kbc said:**
> 
Setting up apache2-common (2.0.55-4ubuntu4) ...
Setting Apache2 not to start, as something else appears to be using Port 80. To allow apache2 to start, set NO_START to 0 in /etc/default/apache2. Apache2 has been set to listen on port 80 by default, so please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.


Do you also have apache (version1.3, not apache2) installed as well?

---

### Post by pavel_kbc on 2006-11-27
ok i remove them .. i am not sure what version is it :S

---

### Post by pavel_kbc on 2006-11-27
i installed the php5 but its not working .. its not showing page. its telling   me to save the page. please help :(

---

### Post by az on 2006-11-27
> **pavel_kbc said:**
> i installed the php5 but its not working .. its not showing page. its telling   me to save the page. please help :(

You need to have libapache2-mod-php5 if you are running apache2 and php5.  Be sure you have the correct version.

---

### Post by shin on 2006-11-28
Is there still this error about port 80 that is already used?

Post output of
```
dpkg -l | grep apache
```

and

```
sudo /etc/init.d/apache2 restart
```

---

### Post by pavel_kbc on 2006-11-28
> **shin said:**
> Is there still this error about port 80 that is already used?

Post output of
```
dpkg -l | grep apache
```

and

```
sudo /etc/init.d/apache2 restart
```
root@r00t-server:/home/r00t# dpkg -l | grep apache
ii  apache                                     1.3.34-4ubuntu1               versatile, high-performance HTTP server
ii  apache-common                              1.3.34-4ubuntu1               support files for all Apache webservers
ii  apache2-common                             2.0.55-4ubuntu4               next generation, scalable, extendable web se
ii  apache2-mpm-prefork                        2.0.55-4ubuntu4               traditional model for Apache2
ii  apache2-utils                              2.0.55-4ubuntu4               utility programs for webservers
ii  libapache2-mod-auth-mysql                  4.3.9-2.1ubuntu1              Apache 2 module for MySQL authentication
rc  libapache2-mod-php4                        4.4.2-1.1                     server-side, HTML-embedded scripting languag
ii  libapache2-mod-php5                        5.1.6-1ubuntu2.1              server-side, HTML-embedded scripting languag
root@r00t-server:/home/r00t# sudo /etc/init.d/apache2 restart
root@r00t-server:/home/r00t# 

isnt working :(

---

### Post by pavel_kbc on 2006-11-28
root@r00t-server:/etc/bluetooth# dpkg -l | grep apache
ii  apache                                     1.3.34-4ubuntu1               versatile, high-performance HTTP server
ii  apache-common                              1.3.34-4ubuntu1               support files for all Apache webservers
ii  apache2                                    2.0.55-4ubuntu4               next generation, scalable, extendable web se
ii  apache2-common                             2.0.55-4ubuntu4               next generation, scalable, extendable web se
ii  apache2-mpm-prefork                        2.0.55-4ubuntu4               traditional model for Apache2
ii  apache2-utils                              2.0.55-4ubuntu4               utility programs for webservers
ii  libapache2-mod-auth-mysql                  4.3.9-2.1ubuntu1              Apache 2 module for MySQL authentication
rc  libapache2-mod-php4                        4.4.2-1.1                     server-side, HTML-embedded scripting languag
ii  libapache2-mod-php5                        5.1.6-1ubuntu2.1              server-side, HTML-embedded scripting languag
root@r00t-server:/etc/bluetooth# 


any budy ?

---

### Post by az on 2006-11-28
You are running two versions of apache.  Remove one.

I suggest you keep apache2 and remove apache.

---

### Post by pavel_kbc on 2006-11-29
root@r00t-server:/etc/apache2/mods-enabled# apt-get remove apache
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@r00t-server:/etc/apache2/mods-enabled# sudo a2enmod php5
This module is already enabled!

---

### Post by shin on 2006-11-30
Apache still not working?
Check if there are any sites settings enabled
```
ls /etc/apache2/sites-enabled/
```

There should be at least 000-default symlink.

Also check if there are any listen ports in
```
cat /etc/apache2/ports.conf
```

There should be something like Listen 80

After removing apache (the one that you removed) restart apache2
```
sudo /etc/init.d/apache2 force-reload
```

and try connecting to localhost

If it's not working - check error logs
```
cat /var/log/apache2/error.log 
```

---

### Post by pavel_kbc on 2006-11-30
root@r00t-server:/home/r00t# ls /etc/apache2/sites-enabled/
000-default
root@r00t-server:/home/r00t# cat /etc/apache2/ports.conf
Listen 127.0.0.1:80
root@r00t-server:/home/r00t# sudo /etc/init.d/apache2 force-reload
root@r00t-server:/home/r00t# cat /var/log/apache2/error.log
[Thu Nov 30 09:06:15 2006] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations
[Thu Nov 30 09:11:34 2006] [error] [client 127.0.0.1] File does not exist: /var/www/livehelp, referer: [http://localhost/](http://localhost/)
[Thu Nov 30 09:11:34 2006] [error] [client 127.0.0.1] File does not exist: /var/www/a.css, referer: [http://localhost/](http://localhost/)
[Thu Nov 30 09:11:34 2006] [error] [client 127.0.0.1] File does not exist: /var/www/livehelp, referer: [http://localhost/](http://localhost/)
[Thu Nov 30 09:11:34 2006] [error] [client 127.0.0.1] File does not exist: /var/www/livehelp, referer: [http://localhost/](http://localhost/)
root@r00t-server:/home/r00t#

---

