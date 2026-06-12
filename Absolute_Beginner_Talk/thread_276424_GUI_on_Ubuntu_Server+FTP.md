---
title: "GUI on Ubuntu Server+FTP"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by skewh on 2006-10-12
Hey everyone!
I'm thinking of installing Ubuntu server, but I have a concern about how there is no GUI preinstalled. I've been told that it will download off the net when I type in a command, but is there anything else I need to do to activate it and will it be the same GUI as on the desktop version? Also, is there an FTP server built in and if so, where do I configure it/find one if there is none. Thank you very much!!!

skewh

---

### Post by Crashmaxx on 2006-10-12
Why do you want to use the server version? It is the same as the desktop version, but without a lot of packages and a little more security stuff by default. Depending on what you want to do, you may just want to install the normal, desktop version and install the ftp server on that. I don't believe an ftp server is installed by default. But I remember a how-to guide to install and configure one around here. I don't think its very hard to do.

EDIT: Here is the link to the how-to, the basics are simple, but the rest might overwhelm you.
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by FizDev on 2006-10-12
To get the GUI and everything like the Ubuntu Desktop version, just type
```
sudo aptitude update
```
(or apt-get, wichever you use)
```
sudo aptitude install ubuntu-desktop
``` (Gnome)
or
```
sudo aptitude install kubuntu-desktop
``` (KDE)
or
```
sudo aptitude install xubuntu-desktop
``` (Gnome)

The last 3 depends on wich GUI you prefer, the default one is Gnome

Edit : Oh and about the FTP server, I don't know if there is any (probably) but all you have to do is search for one in the repository
```
aptitude search ftp server
```
Then just pick the one you prefer and install it ;)

---

### Post by skewh on 2006-10-12
Thanks for your reply! But here's what I want to do: Get a webserver, PHP, MySQL, phpMyadmin, and FTP working, so which version would be the easiest to accomplish these tasks?

---

### Post by FizDev on 2006-10-12
Any of the GUI will work just fine, but I would recommend Gnome :P

For directions on how to install/configure PHP, MySQL and Apache, check there[URL="https://help.ubuntu.com/community/ApacheMySQLPHP"] 
https://help.ubuntu.com/community/ApacheMySQLPHP[/URL]

For the FTP server, check
[https://help.ubuntu.com/community/FtpServer?highlight=%28Server%29%7C%28FTP%29]("https://help.ubuntu.com/community/FtpServer?highlight=%28Server%29%7C%28FTP%29")

---

### Post by skewh on 2006-10-12
So I can do all of the things I want to do using the Desktop version, correct?

---

### Post by Crashmaxx on 2006-10-12
Yes, correct, you just will have a lot of extra stuff you don't need installed too, but it might be easier for you to use. You can remove the extra stuff easily so no big deal.

---

