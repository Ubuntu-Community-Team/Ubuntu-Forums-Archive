---
title: "apache update"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by bigjoe7 on 2007-05-14
Hi i'm trying to update my version of apache to what I believe is the latest version.

Currently running Ubuntu 6.06 LTS (Dapper Drake) as a LAMP server with a website / forum attached.  Very happy with the performance so far and enjoying the Ubuntu experience.

I have run Nikto (pen test http tool) against a dev server on my lan which is a like for like copy of a live website .  Nikto reveals the following:-

>  Scan is dependent on "Server" string which can be faked, use -g to override
+ Server: Apache/2.0.55 (Ubuntu) PHP/5.1.2
+ Allowed HTTP Methods: GET,HEAD,POST,OPTIONS,TRACE
**+ Apache/2.0.55 appears to be outdated (current is at least Apache/2.2.3). Apache 1.3.33 is still maintained and considered secure.**
+ PHP/5.1.2 appears to be outdated (current is at least 5.1.6)
+ / - TRACE option appears to allow XSS or credential theft. See [http://www.cgisecurity.com/whitehat-mirror/WhitePaper_screen.pdf](http://www.cgisecurity.com/whitehat-mirror/WhitePaper_screen.pdf) for details (TRACE)
+ 2673 items checked - 1 item(s) found on remote host(s)
+ End Time:        Mon May 14 20:08:02 2007 (12 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

-

Ok so i have checked [http://httpd.apache.org/](http://httpd.apache.org/), and reveals the latest version is indeed a little newer than what nikto regards (Apache 2.2.4 ).

I have run the following commands from the CLI to upgrade apache.

> sudo aptitude update && sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 3B in 1s (3B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  linux-image-server
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

and also

> sudo apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
apache2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


What am i doing wrong?
Why I cant upgrade to latest version of apache?
I'm sure im being a n00b!

---

### Post by foresth on 2007-05-14
The "apt-get install apache2" is telling you that you have the newest version because there isn't neither the 2.2.x version nor any newer version than 2.0.55 in the repository. But I wouldn't worry about this at all because you probably don't need the 2.2.x version. The 2.2.x version of Apache is quite different from the 2.0.x version and the 2.0.x version is now accepted as the most proper version of Apache for using along with PHP.

---

### Post by az on 2007-05-14
The version of apache2 in Ubuntu is up-to-date with security patches.  That warning should only apply to someone who is running a version straight from the apache2 upstream source (nobody does that)

---

### Post by bigjoe7 on 2007-05-14
Thanks foresth,az

Thats what I was after - apache with the latest security patches.

---

### Post by az on 2007-05-14
[http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.0.55-4ubuntu2.1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.0.55-4ubuntu2.1/changelog)

---

### Post by esoterica on 2007-05-14
I have a related question, no sense opening a new thread for, sorry if this seems as a hijack of this post.

I've installed Ubuntu desktop version on my laptop since this is primarily what I'm using it as, however, I need to run and test PHP files on this Desktop. I didn't install LAMP because I wanted the GUI features of the desktop version. What I haven't found though is an option in the software list to add Apache, MySQL and PHP to the Desktop version. I don't need to open ports or use this as a true server, just need a easy way I can edit PHP files and see the results on the same system without the hassle of uploading them to test on my actual web server.

I know I could physically compile the Apache source code etc.. and install it that way, but I'd prefer to keep everything pure and supported with in Ubuntu and it's way of doing things. If possible I'd also prefer to only install Apache 1.3.37 MySQL 4.1.21-standard and PHP 4.4.6 since this is what my live server is running on.

Am I just not seeing the option in the Ubuntu packages to add this or isn't this an available option or ability?

---

### Post by NumberOne on 2007-05-14
You could always add the packages that you want individually using synaptic installer.  What I did was to install the Lamp server than add the Ubuntu desktop.  This was alot easier.

---

### Post by esoterica on 2007-05-14
Thanks, I thought about doing that, but my familiarity with Linux in the past led me to fear that option in having to then configure my video drivers and everything else GUI associated which I've found to be a nightmare in days now seemingly behind the Linux Community. To be honest, I was blown away when I installed Ubuntu and it just worked. I wasn't expecting that and it caught me a little off guard.

I thought I'd then just be able to add Apache and PHP easily from the installer, but I don't see it as an option, I've enabled all the repositories, are you saying it is in there somewhere and I just over looked it (it's a lot to sift through so I suppose that's possible).

I'll probably sooner than later end up completely hosing this install up by just trying to play around with it and need to reinstall everything from scratch again anyhow, next time around I'll keep in mind that it may be easier to install LAMP first and add the GUI afterwards, in the mean time though, since I'm where I'm at and it is working I'll want to do it a little backwards from how you suggested.

I found the Synaptic Package Manager thing you mention, I see under "World Wide Web" 3 separate listings, the differences of the 3 mean nothing to me so I don't understand which of these options is recommended?

World Wide Web

World Wide Web (mutliverse)

World Wide Web (universe)

What's the difference between all of these?

---

### Post by az on 2007-05-14
It is easy to install the LAMP stack on top of a GUI.  Easier in fact than installing a server and then adding the desktop on top of that.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

OR

You can also use the synaptic manager and install by task.  Synaptic - mark package by task - LAMP.  The press apply and you have a LAMP stack.

As far as repositories, everything is in main, so you don't need to enable universe or multiverse.

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by esoterica on 2007-05-14
Excellent!

> 
It is easy to install the LAMP stack on top of a GUI. Easier in fact than installing a server and then adding the desktop on top of that.


I thought it would be, but just couldn't find the information, that link was exactly what I wanted and was looking for, perfect, thanks!

---

