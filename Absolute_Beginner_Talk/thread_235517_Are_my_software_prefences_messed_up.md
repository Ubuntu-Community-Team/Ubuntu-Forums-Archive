---
title: "Are my software prefences messed up?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by karohan on 2006-08-13
I just recently installed Ubuntu Dapper Drake (around three days ago). I ran the program Easy Ubuntu, since it was supposed to install lots of useful stuff for beginners, like me (this is my first linux installation ever). I just followed the directions when installing, and after I installed it, I realized that when I went to System>Administration>Software Properties that all of my repositories under the Installation Media tab were version 5.10. So they'd say either Ubuntu 5.10, Ubuntu 5.10 Updates, etc etc. I don't if its supposed to be 5.10 or not, since I installed Dapper Drake which is 6.06. Does anyone know whether my installation of Easy Ubuntu made those changes, if any changes were made at all. I remember that when installing it, it did say that it would have to modify my repositories, but once I uninstalled Easy Ubuntu, all of the items in the installation tab still were 5.10. Is there any way to change this?

---

### Post by Ziox on 2006-08-13
> **karohan said:**
> I just recently installed Ubuntu Dapper Drake (around three days ago). I ran the program Easy Ubuntu, since it was supposed to install lots of useful stuff for beginners, like me (this is my first linux installation ever). I just followed the directions when installing, and after I installed it, I realized that when I went to System>Administration>Software Properties that all of my repositories under the Installation Media tab were version 5.10. So they'd say either Ubuntu 5.10, Ubuntu 5.10 Updates, etc etc. I don't if its supposed to be 5.10 or not, since I installed Dapper Drake which is 6.06. Does anyone know whether my installation of Easy Ubuntu made those changes, if any changes were made at all. I remember that when installing it, it did say that it would have to modify my repositories, but once I uninstalled Easy Ubuntu, all of the items in the installation tab still were 5.10. Is there any way to change this?

Open up sources.list file:

gksu gedit /etc/apt/sources.list

and find all instances of "breezy", using find and replace, replace "breezy" with "dapper"

You might've used the wrong version of easyubuntu, but i'm not sure about that.

---

