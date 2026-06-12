---
title: "sudo apt-get question"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by thinhlegolas on 2005-11-01
How do you guys know which ftp or http to include in /etc/sources.lst?

Also how do you guys know exactly the name of the package you want to install... for example, how do you know sudo apt-get install acroread will install Acrobat Reader?

Also the how do you choose which version to install... the other day i was doing a 

sudo apt-get install unrar

and it installed the old version, i had to google for the newer version

---

### Post by Dr. Nick on 2005-11-01
The servers should be setup for you while installing. If you dont know the name of a package use synaptic and search in titles and descriptions, their are other ways aswell but this is easy. It will usually install the newest version it has available, but that inst always the newest version made. It takes a little time to get the most current version to the servers

---

### Post by 23meg on 2005-11-01
[QUOTE=thinhlegolas]

Also how do you guys know exactly the name of the package you want to install... for example, how do you know sudo apt-get install acroread will install Acrobat Reader?
[/QUOTE]

Do a description search in Synaptic. Hit "Search" and in the "Look In" combo box choose "Description and Name".

---

### Post by az on 2005-11-01
For a stable release, the versions of the packages do not change. You would have to change your repositories to point to a newer release.  You should wait untill Dapper is at least in preview (four and a half months from now) before doing that with Dapper.  But, if you are runnnig Hoary and wand to get a Breezy package, add the breezy repos.

---

### Post by aysiu on 2005-11-01
Read this:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

