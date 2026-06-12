---
title: "display_php_page"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by tiendn on 2007-03-27
Hi!
I am a Ubuntu and PHP beginner, I have got a problem when I want display php pages.
I have written a PHP pages, when I use 'localhost' for displaying that pages, but It not displayed 
and it downloads the file php
I don't understand this problem...
                                                                                                                       thanks!

---

### Post by compmodder26 on 2007-03-27
Are you sure you've installed the php apache module?  Search synaptic for "apache php".  Make sure you have a green box next to the package named "libapache2-mod-php5"

---

### Post by tiendn on 2007-03-27
I have installed libapache2-mod-php5 package when I installed PHP. but that problem is still coming...

---

### Post by compmodder26 on 2007-03-27
Check in /etc/apache2/mods-enabled and make sure there are symbolic links for "php5.conf" and "php5.load"

---

### Post by tiendn on 2007-03-27
when I check /etc/apache2/mods-enabled, there are not "php5.conf" and "php5.load"
but there are "php5.conf" and "php5.load" in /etc/apache2/mods-available...
How can I repair that problem?

---

### Post by compmodder26 on 2007-03-27
Good, we should be able to lick the problem in this next step.  Paste the following two commands into a terminal:

```
sudo ln -s /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/php5.conf
sudo ln -s /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/php5.load
```

After that, restart apache:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by tiendn on 2007-03-27
Thak you very much! I repaired that probem!

---

### Post by compmodder26 on 2007-03-27
Good to hear.

---

### Post by aiserv on 2007-04-06
I have the same problem!
Have the libapache2-mod-php5 installed
"php5.conf" and "php5.load" are in the /etc/apache2/mods-enabled folder
Here's the bash response, maybe it will help you to know the problem?
```
ais@desktop:~$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of apache 2.0 web server...
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98): make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
ais@desktop:~$
```
Apache is working, just .php files doesnt shows.
It started after i tryed to install Perl.
by the way .pl files doesnt works as well, but its not a big problem :)

Sorry for my english!

---

