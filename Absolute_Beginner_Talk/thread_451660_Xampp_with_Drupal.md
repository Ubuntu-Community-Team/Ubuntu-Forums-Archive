---
title: "Xampp with Drupal"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by bren21 on 2007-05-22
Hi, I am trying to get Drupal installed on my xampp server, however I am getting the error ```
The Drupal installer requires write permissions to ./sites/default/settings.php during the installation process.
```

I checked to see if the file it is referring to was in the right directory, and it was. I am not sure why this is happening. If anyone else has gotten Drupal installed on Xampp, please let me know how you did it.

---

### Post by jingo811 on 2007-05-22
I gave up on XAMPP after their sloooow support.  So now I'm learning to LAMP.
Install time for me:

WAMP = ~15 min
XAMPP = ~5 min
LAMP the aptitude way = ~5 sec

Configurations and troubleshooting not included.


To install php 5, apache 2.2 and mysql 5 (server)
```
sudo aptitude install php5 apache2 mysql-server
```

Troubleshooting and setup guide:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


I had to do this to make my Apache+PHP run properly:
> If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then edit gksudo gedit /etc/apache2/apache2.conf and add ServerName localhost at the end of the file 

I figure using LAMP over XAMPP will be easier to add extra stuff like Drupal.

---

### Post by bren21 on 2007-05-22
I had tried that, however I could not get php to work on it, so I decided just to take the easy way out and install xampp

---

### Post by annda on 2007-05-22
you can always try installing drupal as root but sooner or later you will run into permission trouble with the files.

check this guide out for permissions handling:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by bren21 on 2007-05-22
how would I do that? It installs when I go to the directory that I extracted drupal (when i am in firefox). How do you become root for that? Besides, the directory I am installing it in is linked to my xampp allowing me to put stuff in it when I am not root.

---

### Post by jingo811 on 2007-05-23
I'm telling you XAMPP is bad mojo.  They have wired things differently to what the real AMP setups are for Windows as for Linux.  Troubleshooting for XAMPP is snail-mail business.

Invest your time into installing the real LAMP instead of a fake make pretend one.  It's worth the time in the long run later on.

---

### Post by bren21 on 2007-05-23
> **jingo811 said:**
> I gave up on XAMPP after their sloooow support.  So now I'm learning to LAMP.
Install time for me:

WAMP = ~15 min
XAMPP = ~5 min
LAMP the aptitude way = ~5 sec

Configurations and troubleshooting not included.


To install php 5, apache 2.2 and mysql 5 (server)
```
sudo aptitude install php5 apache2 mysql-server
```

Troubleshooting and setup guide:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


I had to do this to make my Apache+PHP run properly:


I figure using LAMP over XAMPP will be easier to add extra stuff like Drupal.

Well I decided to do what you said, and I got the same error as you, but it still seems to work. When I type localhost it goes to the default page, so do I still have to add that to the apache2.conf? If so, do I simply add ```
localhost
``` to the end or ```
ServerName localhost
```? Thanks for your help!

---

### Post by annda on 2007-05-23
if a page is displayed when you go to localhost, you are all set. put your own pages in /var/www - if you put there an index.html or index.php it will be displayed instead of the default (or directory listing, whichever you get to see after install).

---

### Post by bren21 on 2007-05-23
I was looking on the forums, and saw that someone mentioned this was the wrong way to install it. Can anyone confirm this? If so, could you point me to a tutorial with the correct method. Thanks a lot.

---

### Post by bren21 on 2007-05-23
Okay, I managed to setup the server the correct way, and still ran into the problem, but fixed it. All I needed to do was change the permissions on the file to write. It wasn't a problem with Xampp.

---

