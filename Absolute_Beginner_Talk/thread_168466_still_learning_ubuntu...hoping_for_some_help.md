---
title: "still learning ubuntu...hoping for some help"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by chrisjm00 on 2006-04-30
ive only had ubuntu for a few days..but i want to start installing some programs. how do i install programs from packages?

---

### Post by Roel Groeneveld on 2006-04-30
[QUOTE=chrisjm00]ive only had ubuntu for a few days..but i want to start installing some programs. how do i install programs from packages?[/QUOTE] 

You mean packages from the Ubuntu software repositories? 
Try following the explanation on the wiki: 
[https://wiki.ubuntu.com/InstallingSoftware#head-82ee502162e81ddca57bfba9281ad97c39fd7fbe](https://wiki.ubuntu.com/InstallingSoftware#head-82ee502162e81ddca57bfba9281ad97c39fd7fbe) 
Using software from the repositories is recommended. 

If you found a package you want to install by hand (e.g. the old-fashioned way, or Windows/Mac way): 
[https://wiki.ubuntu.com/InstallingSoftware#head-c0628aa246e0b55ea2009705d1b5a84ede8736b5](https://wiki.ubuntu.com/InstallingSoftware#head-c0628aa246e0b55ea2009705d1b5a84ede8736b5)

---

### Post by savas on 2006-04-30
Hi. You can use Synaptic (System->Administration->Synaptic Package Manager) to install packages. You don't have to download packages seperatly. It will download for you. Or you can use apt-get in terminal. Syntax is like below;

sudo apt-get install <package name>

If you want to install a deb package that you have already downloaded, you can use,

sudo dpkg -i <package name>

---

