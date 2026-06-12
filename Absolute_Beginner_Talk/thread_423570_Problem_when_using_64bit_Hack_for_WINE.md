---
title: "Problem when using 64bit Hack for WINE"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by PleaseEnjoyThis on 2007-04-26
To make WINE compatible for my 64bit I had to install these libraries, but I got this.  More detail on what I was doing...[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)


fer:~$ sudo apt-get install ia32-libs lib32asound2 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

help would be lovley

---

### Post by dubrict on 2007-04-26
in synaptic package manager, click on "settings" - > "repositories" and select all the checkboxes.  Thisi will enable all the repositories to download from.  When you're done you need to click "reload" in synaptic's main window.
If it's still missing, I don't know what to tell you.

---

