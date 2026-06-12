---
title: "How do you do this with wine?!?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by flameboy2992 on 2006-09-24
Ok I want wine to work and be able to run windows programs in ubuntu but what always happens when i try to install wine is it says cant run i386 programs and there was this ubuntu thing on the website about going into system> administrator>synaptic package manager and add a repository and i did all that crap added the website reloaded it and everything but what do i do now i still cant run windows programs?

---

### Post by aysiu on 2006-09-24
Read this:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by flameboy2992 on 2006-09-24
ok in that tutorial it says when he clicks on filezilla it starts automaticaly but mine doesnt it just says...."Couldn't display "/home/miles/Desktop/FileZilla_2_2_27_setup.exe".....how do i get it so it starts up automaticaly when i double click on it? and if i try to make it open with wine like go right click properties>openwith>customcommand>browse and go and find wine under file system it says....."Could not find '/usr/share/app-install/desktop/wine.desktop".....what should i do?

---

### Post by aysiu on 2006-09-24
Do you definitely have Wine installed?

---

### Post by visvak on 2006-09-24
just completely remove wine and reinstall it using this guide - 

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+setup+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=howto+setup+wine)

ive done it on many machines with the help of this guide and not one ahs gone wrong so far.

---

### Post by CatKiller on 2006-09-25
> **flameboy2992 said:**
> ok in that tutorial it says when he clicks on filezilla it starts automaticaly but mine doesnt it just says...."Couldn't display "/home/miles/Desktop/FileZilla_2_2_27_setup.exe".....how do i get it so it starts up automaticaly when i double click on it? and if i try to make it open with wine like go right click properties>openwith>customcommand>browse and go and find wine under file system it says....."Could not find '/usr/share/app-install/desktop/wine.desktop".....what should i do?

You've picked the wrong file to use as the "Open With" application. You should just be able to write ```
wine
``` in the "Use a custom command" box. Otherwise, the appropriate path to the wine command is, I believe, ```
/usr/bin/wine
```

---

