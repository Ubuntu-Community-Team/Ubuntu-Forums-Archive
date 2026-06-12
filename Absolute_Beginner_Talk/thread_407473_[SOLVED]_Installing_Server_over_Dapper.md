---
title: "[SOLVED] Installing Server over Dapper"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2007-04-12
Afternoon,

I'm looking for a little advice that I could not seem to find an answer to in a forum search.

First a little info:

I'm a new Ubuntu convertee. :)

I'm currently dual booting WinXP and Dapper.

(I did dive straight into Ubuntu, but then had to revert to a dual boot to get some work done.)

One of the reasons for keeping WinXP at the moment is because I'm running a WAMP server.

I'm currently downloading the Dapper Server version.

My question is, how do I go about installing it ?

Do I remove my existing Dapper install, then install the serever, then activate the graphical interface.

Or can I install the applications that I need from the Server CD over the top of my current Dapper installation ?

(I only really need Apache, Perl, PHP, mySQL and can do without some of the more esoteric applications.)

Or, a third option would be to download the tarballs and install from there.

All opinions appreciated.

Thanks in advance !

---

### Post by Malakia on 2007-04-12
If I remeber correctly the Ubuntu server CD has a option to install a LAMP server. Doing a server install will give a minimal ubuntu interface with no gui.

---

### Post by WorldTripping on 2007-04-12
Thanks for the reply.

I've heard the Server CD has a LAMP install.

But can I just install the LAMP bit off the CD on top of my Dapper installation?

Or do I have to remove my current Dapper installation, install the server, reinstall the desktop, then reinstall all of my currently working apps ?

Cheers.

---

### Post by andydread on 2007-04-12
Type this in a terminal window.  I know. .. . its just easier to 
tell you what to do in a terminal rather than click this click that.   

```
sudo apt-get install apache2  php5 mysql-server-5.0 php5-mysql.
```
install ssl
```
sudo apt-get install openssl
```
go to [http://www.webmin.com](http://www.webmin.com) and download webmin 
if you want to manage the servers easily.
Save the .deb file and doubleclick it to install it. 

also install phpmyadmin if you wish

TO config mysql from gnome u may install (GUI)
```
sudo apt-get install mysql-admin
```

the icon will show up under applications->system tools. as MYSQL Administrator

Have fun.

---

### Post by WorldTripping on 2007-04-12
Thanks for that.

I assume that this procedure will connect to a repository, and download/install the packages.

Thats kinda where I fall down, in that I only have a very slow dialup connection at home, and am currently using the computer at work to download the server package.

Can I install these packages from the Server CD, or should I just install the LAMP server, and then activate the gui ?

(Incidently I don't need ssl as it's a for a development enviroment, and I don't need the web-admin, as it's a limited set of sites, and I'm quite happy to configure the sever manually. The phpmyadmin is useful though)

Cheers for the advice.

---

### Post by Maestro23 on 2007-04-12
Dapper Server Guide: [https://help.ubuntu.com/6.06/](https://help.ubuntu.com/6.06/)

---

### Post by WorldTripping on 2007-04-12
Cheers for all the help.

Looks like I know what I'll be doing this weekend.

:D

---

### Post by opengovtv on 2007-04-12
> **andydread said:**
> Type this in a terminal window.  I know. .. . its just easier to 
tell you what to do in a terminal rather than click this click that.   

```
sudo apt-get install apache2  php5 mysql-server-5.0 php5-mysql.
```
install ssl
```
sudo apt-get install openssl
```
go to [http://www.webmin.com](http://www.webmin.com) and download webmin 
if you want to manage the servers easily.
Save the .deb file and doubleclick it to install it. 

also install phpmyadmin if you wish

TO config mysql from gnome u may install (GUI)
```
sudo apt-get install mysql-admin
```

the icon will show up under applications->system tools. as MYSQL Administrator

Have fun.

i love the support groups here. thanks for this info. i had the same question as the OP and will try this myself. thanks.

---

