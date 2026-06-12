---
title: "Ubuntu Server"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Technogeek on 2007-07-11
Ok I want to run Ubuntu as a server problem is i have no idea how to run Ubutu As A Server with out a gui I have no clue?? i built the server my with a 1 TB external hdd and a 250 GB internal i use broad band dsl with a Linksys Router my dsl is Dynamic can any one help im in distress!!!!


thank you 

Technogeek
[COLOR="Red"]**(LINUX IS A REALITY)**[/COLOR]:popcorn:

---

### Post by pyros on 2007-07-11
> **Technogeek said:**
> Ok I want to run Ubuntu as a server problem is i have no idea how to run Ubutu As A Server with out a gui I have no clue?? i built the server my with a 1 TB external hdd and a 250 GB internal i use broad band dsl with a Linksys Router my dsl is Dynamic can any one help im in distress!!!!


thank you 

Technogeek
[COLOR="Red"]**(LINUX IS A REALITY)**[/COLOR]:popcorn:

That would depend on what you wanted to do with the server...

---

### Post by Technogeek on 2007-07-11
> **pyros said:**
> That would depend on what you wanted to do with the server...


I want to use it as a ftp server for my home network and for my friends in FLA. to log in and use it


Technogeek

---

### Post by atria on 2007-07-11
If the ip is dynamic, you can set up a dynamic dns for it. Companies like dyndns.com offer the service for free.

Ubuntu server comes with no gui, you will be managing the server solely with commandline through SSH.

So basically, if you're going to manage the server, you have to be at least proficient with basic linux commands.
It is possible to install a gui on the server and VNC into it, but alas you'll still need basic commandline knowledge to set up the ftp server.

vsftpd is a good ftp daemon, you might want to check it out.

Good luck ;)

---

### Post by pyros on 2007-07-11
> **Technogeek said:**
> I want to use it as a ftp server for my home network and for my friends in FLA. to log in and use it


Technogeek

Have a look [here](http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server) to start with. I hope you are prepared for some reading before you have this working.

---

### Post by pyros on 2007-07-12
if you just want to install ubuntu desktop, you can still install a server on top of it. I know of at least two ftp server  guis in the repositories:
pureadmin
gproftpd

---

