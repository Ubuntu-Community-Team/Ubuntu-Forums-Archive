---
title: "Automatix issues"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Climacusdoubt on 2006-08-06
This is the second computer that I have installed automatix.  The second intall i am having issues with.  When I enter "sudo apt-get install automatix" this is the response that I get:

climacusdoubt@laptop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix

I did not have this issue on the first install and was hoping that someone could help.

---

### Post by catlett on 2006-08-06
From the automatix thread [http://ubuntuforums.org/showthread.php?t=223087](http://ubuntuforums.org/showthread.php?t=223087)

> To install automatix do the following (3 steps):
Open up terminal and paste the following 3 commands one after the following:
Code:

```
wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer) 
``````
chmod 755 ~/automatix-installer
``````
 ./automatix-installer
```

When the installer finishes successfully (without any errors) and you get back to command prompt, run Automatix from Applications --> System Tools in Ubuntu, Main Menu --> System in Kubuntu/Xubuntu Dapper

The above installer checks the version of Ubuntu installed on your computer and your desktop environment (Gnome/KDE/XFCE) and adds the suitable repository to your sources.list, updates it and installs automatix. 
After you have used this installer once, you do not need to use it again because automatix will get updated automatically (through update manager) every time a new version is released..

__________________

---

