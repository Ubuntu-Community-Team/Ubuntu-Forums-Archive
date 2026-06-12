---
title: "screen resolution question"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by tuan209 on 2007-07-10
Hi,

Sorry if this question has been asked many times before, but I am totally lost.  I just installed ubuntu for the very first time, and this is the first time ive ever used linux so excuse me if I post many noobs/dumb questions.  The problem I am currently having is that my max resolution is 1024x768, and I would like to set it to 1440x900.  Ive seen post about editing your xorg.conf, but I dont know what that is or how to access it.  I went to applications -> accessories -> terminal -> and typed sudo gedit/etc/x11/xorg.conf but it keeps asking for a password.  I try to type in my password (which consists of numbers) but I can not type anything.  Im totally lost.  Could someone walk me through this?

Tuan

---

### Post by Inxsible on 2007-07-10
It will not show you the password in *...but it is definitely taking in the password. Just complete the password and hit 'Enter'

---

### Post by Inxsible on 2007-07-10
Alternatively, since you are using a GUI app (gedit), you can use :
 
```
gksudo gedit /etc/X11/xorg.conf
```This will give you a nice GUI box which will take in your password and show you black dots for each character.
 
Also in your code, you are using x11 which would be incorrect since Linux is case sensitive. There should also be a space between gedit and /etc.....

---

