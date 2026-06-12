---
title: "Starting apache server"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-04-23
I can't get php working on my system now. Seems like the settings are messed up now as I was able to run it properly few days ago. 

Can someone please take a look at this and tell me what is going wrong :

$ sudo /etc/init.d/apache2 start
 * Starting web server (apache2)...                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by az on 2007-04-23
Check to see what apache packages you have intstalled.  Did you inadvertently install apache alongside apache2 while trying to install libapache2-mod-php5?  Make sure you only keep apache2 (not apache version 1.3) and php5 (libapache2-mod-php5, not libapache-mod-php5)

---

### Post by Joseaa on 2007-04-23
well, I am  not clever enough to recollect what I actually did :P  Is there any command to see what has been installed ? If so, please do let me know( commands) how to rectify it also.

---

### Post by Joseaa on 2007-04-23
Anyone. Please help !

---

### Post by az on 2007-04-23
dpkg -l |grep apache

---

### Post by Joseaa on 2007-04-23
Here is the output : 

ii  apache                                     1.3.34-4.1                             versatile, high-performance HTTP server
ii  apache-common                              1.3.34-4.1                             support files for all Apache webservers
ii  apache2-mpm-prefork                        2.2.3-3.2build1                        Traditional model for Apache HTTPD 2.1
ii  apache2-utils                              2.2.3-3.2build1                        utility programs for webservers
ii  apache2.2-common                           2.2.3-3.2build1                        Next generation, scalable, extendable web se
ii  libapache2-mod-php5                        5.2.1-0ubuntu1                         server-side, HTML-embedded scripting langua

---

### Post by az on 2007-04-23
sudo apt-get remove apache apache-common

sudo /etc/init.d/apache2 restart

---

### Post by Joseaa on 2007-04-23
Thanks a lot.

---

### Post by Pobega on 2007-04-23
You also may want to download sysv-rc-conf and check to make sure Apache2 isn't starting at boot time. If it is starting, just use the space bar to turn it off.

---

### Post by az on 2007-04-23
> **Pobega said:**
> You also may want to download sysv-rc-conf and check to make sure Apache2 isn't starting at boot time. If it is starting, just use the space bar to turn it off.

Any reason you wouldn't want it to start on boot?

---

