---
title: "Webcam in Ubuntu"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by ExBuM on 2008-04-14
I have a Dell sp2208WFP monitor which came with a webcam. I'm trying to figure out how to use it in ubuntu but I'm not getting too far. Apparently it's supported by "linux uvc drivers and tools" ([http://linux-uvc.berlios.de/#download](http://linux-uvc.berlios.de/#download) id: 05a9:2643) but I still don't actually know how to access it. Like what program to use or if it's actually being detected. I tried ekiga but it said there was no video detected. So how do I get this thing to work? 
Thanks in advance

---

### Post by talsemgeest on 2008-04-14
Ok it says you need to install from the svn. Svn is a program that takes the latest source code from the developers. So if you have all the dependancies and svn installed you can run the command which will download the source code into your home directory. Cd into the directory, ./configure , make, sudo make install.

Hope this helps :)

---

### Post by ExBuM on 2008-04-14
I ran this command ```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
``` but I'm getting ```
svn: Can't connect to host 'svn.berlios.de': Connection timed out

``` so I guess I'll just try again later (unless I did something wrong >.>)

---

### Post by talsemgeest on 2008-04-14
Thats weird. Your internet running properly?

---

### Post by ExBuM on 2008-04-14
I think so... I'm on this site, torrenting and using pidgin.

---

### Post by talsemgeest on 2008-04-14
Mmmm... Good to know. I will try the command when I get onto my ubuntu box.

---

