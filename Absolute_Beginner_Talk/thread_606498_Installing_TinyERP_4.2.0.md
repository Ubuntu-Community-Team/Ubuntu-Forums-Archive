---
title: "Installing TinyERP 4.2.0"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by yveslens on 2007-11-08
Hello 
I m NEW on Linux and UBUNTU
should like to install TinyERP 4.20 on ubuntu 7.10.
I ve found tutorial 
[http://www.tinyerp.org/wiki/index.php/Main/ManuelDinstallation](http://www.tinyerp.org/wiki/index.php/Main/ManuelDinstallation)

I ve downloaded the 2 files , i ve made the tar cmmand, but i think it's not good cause i don't find the software

```
 tar -xzvf tinyerp-server-4.2.0-rc2.tar.gz tar -xzvf tinyerp-client-4.2.0-rc2.tar.gz 
~$:sudo su postgres NB: enter le password root 
~$:/home/user/tinyerp-server/bin/tinyerp-server.py -r postgres -w postgres
~#:/home/user/tinyerp-client/bin/tinyerp-client.py 

 
```





Please can somebody help me 

Thanks

---

### Post by mts-fi on 2007-11-29
Try this!

[http://ubuntu.roomandspace.com/](http://ubuntu.roomandspace.com/)

I installed it ok (maybe), but I can't get it working (can't create database).
Please tell me if you can make it work!

---

### Post by kleinerdrache on 2007-11-30
Hi there!

Fine, how did you find my repository?

You can create a database with postgresql, you should add a superuser named 'terp' and a database 'terp' owned by 'terp'. :)  Then you put the password of terp in /etc/defaults/tinyerp-server (or how that file is named) and restart tinyerp, that should work

if you have any troubles feel free to contact me.

Martin

---

### Post by mts-fi on 2007-11-30
Found it from here: [http://tinyerp.org/wiki/index.php/InstallationManual/ServerInstallUbuntu](http://tinyerp.org/wiki/index.php/InstallationManual/ServerInstallUbuntu)
Thank you!

I had my Tinyerp working earlier today. 
I wrote something about my sollution here:  [http://tinyerp.org/forum/topic5215.html](http://tinyerp.org/forum/topic5215.html)

---

### Post by ubername on 2007-11-30
> **kleinerdrache said:**
> Hi there!

Fine, how did you find my repository?

You can create a database with postgresql, you should add a superuser named 'terp' and a database 'terp' owned by 'terp'. :)  Then you put the password of terp in /etc/defaults/tinyerp-server (or how that file is named) and restart tinyerp, that should work

if you have any troubles feel free to contact me.

Martin

Sorry, how do you create a database? I can't find postgresql in any of my menus (although the Tiny-ERP client appears) and typing 'postgresql' in the terminal doesn't work.

---

