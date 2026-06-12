---
title: "Where is my nice GUI Compiz Settings Manager?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-08-31
Compiz installed just fine. The cube works an everything. I just can't configure anything in Compiz, like the zoom distance, the rotate speed, the skydome image etc.

[http://www.ubuntugeek.com/compiz-and-nvidia-on-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/compiz-and-nvidia-on-ubuntu-feisty-fawn.html)
> If you want to configure compiz use the following command

gconf-editorThis gconf-editor sucks and is hard to use

> antsvr@antubuntu:~$ sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-gnome is already the newest version.
E: Couldn't find package compizconfig-settings-manager
antsvr@antubuntu:~$ 




Reference
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)
[http://www.ubuntugeek.com/compiz-and-nvidia-on-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/compiz-and-nvidia-on-ubuntu-feisty-fawn.html)

---

### Post by Yes on 2007-08-31
You mean CompizConfig Settings Manger?

System -> Preferences -> CompizConfig Settings Manager

I thought that that was installed when you installed Compiz, but I might be mistaken.

---

### Post by A-Sylum on 2007-08-31
try installing ccsm compizconfig settings manager and when you install it you can find it under system -> preferences :) good luck!!!

---

### Post by ant2ne on 2007-08-31
> antsvr@antubuntu:~$ sudo apt-get install ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm
antsvr@antubuntu:~$ :(

---

### Post by Julio Viana on 2008-02-02
Try this:
 # sudo apt-get install compizconfig-settings-manager

Then:
 System -> Preferences -> Advanced Desktop Effects Settings (in Ubuntu 7.10)

---

### Post by alwiap on 2008-02-02
once it is installed you can also run the settings manager by clicking alt+f2 (run) and then typing 'ccsm'

---

