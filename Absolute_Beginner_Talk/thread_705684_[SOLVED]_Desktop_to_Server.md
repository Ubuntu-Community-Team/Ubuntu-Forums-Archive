---
title: "[SOLVED] Desktop to Server"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by satterle on 2008-02-23
Currently running a dual boot XP and Feisty Desktop.

Want to set up a localhost development box. What is the best way to set up Apache/MySQL/PHP? Can Desktop be upgraded to Server? I'm looking for the simplest way, being a newby and all.

---

### Post by mytwobears on 2008-02-23
Hi:

You should download the Ubuntu Server version and do a fresh install and choose the LAMP installation option.  I wouldn't try to upgrade your desktop version.  Just install the Ubuntu LAMP server over it.  Here are some instructions for accomplishing that:

[ubuntu-710-gutsy-gibbon-lamp-server-setup.html]("http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html")

---

### Post by satterle on 2008-02-23
Can I still maintain the dual-boot?

---

### Post by HereInOz on 2008-02-23
If you really want to get stuck into setting up a server, check out this how-to on sourceforge:

[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

Should give you all the information you need.  

I can't help you with the question as to whether you can maintain the dual boot, though.  Given that it is a server, why would you want to, as the idea of a server is to be always on.  Nevertheless, a quick install of XP and then Ubuntu server will tell you whether you can still dual boot or not.

---

### Post by Daveski on 2008-02-23
> **mytwobears said:**
> You should download the Ubuntu Server version and do a fresh install and choose the LAMP installation option.  I wouldn't try to upgrade your desktop version.  Just install the Ubuntu LAMP server over it.

Why? I installed Xubuntu (desktop) on an old laptop to act as a server. I have installed MySQL, Apache, PHP, SSH, Postfix, Fetchmail, Dovecote and Webmin and this is doing a great job as a home server with only 256Mb of RAM. Installing the 'server' version is good if you need a quick way to get a server online, but I think you could learn a lot by installing each component yourself.

---

### Post by satterle on 2008-02-28
Found this page to be extremely helpful:


[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)

---

### Post by Dr Small on 2008-02-28
If you wish to setup a localhost on your desktop, check out XAMPP, as it is what I have used for years:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

Dr Small

---

### Post by justleen on 2008-02-28
If you only plan to use is for web-developtment, i wouldnt recommend the server editiion, personally.

THe server version is for running a server, nor for having a GUI interface with editors and what else.

I use the normal desktop version, with AMP installed, so i can do my webdesign off line.
This is on my work laptop, on which i do my day to day work as well, and the fact that mysql and apache are running in the background doenst bother me in the least, since there are no connection made to the servers, except by my locahost..

---

### Post by Oldsoldier2003 on 2008-02-28
> **Daveski said:**
> 
...snip...

 Installing the 'server' version is good if you need a quick way to get a server online, but I think you could learn a lot by installing each component yourself.
yes as long as its not a "production" box i would agree. But if you need a production box in a hurry and are not intimately familiar with the workings of a LAMP server its best to do a install of Ubuntu server and let the installer configure your LAMP server for security reasons. This will prevent some of the more common "ooopses" that could leave you vulnerable.

---

