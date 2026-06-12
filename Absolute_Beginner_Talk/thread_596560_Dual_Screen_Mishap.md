---
title: "Dual Screen Mishap"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by aeqvitas1 on 2007-10-29
I made a pretty stupid mistake when trying to set up the dual screen function on the new version of Ubuntu. I set both screens to be automatically detected on my laptop, and what happened, I think, was that it's trying to use that one screen for both screens. So whenever I turn on my computer, it brings me to a black screen with command prompt...

Is there anyway I can undo what I did, or fix it from the command prompt screen.

(I was trying to hook up my TV as a dual monitor, btw, if you could offer any help there as well)

---

### Post by NT4usB on 2007-10-29
From the command prompt screen:
Ctrl+Alt+F1 and login.
```
cd /etc/X11
ls -al xorg*
``` and look for the file: xorg.conf and (hopefully!) a backup file called xorg.conf~ or xorg.conf.xxxx with a date near before you broke it.
If there is one, you're in luck.
```
 sudo cp xorg.conf bkup.xorg.conf 
```to backup the current one for forensic purposes, then```
sudo cp xorg.conf~ xorg.conf
```The first file(xorg.conf~) being the last good backup you found dated before it broke.
Then```
startx
```or```
sudo startx
```or```
sudo /etc/init.d/gdm restart
```I can never remember which...

If that doesn't work or you don't have a backup, you can try:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from the same login.

---

### Post by Crafty Kisses on 2007-10-29
> **NT4usB said:**
> From the command prompt screen:
Ctrl+Alt+F1 and login.
```
cd /etc/X11
ls -al xorg*
``` and look for the file: xorg.conf and (hopefully!) a backup file called xorg.conf~ or xorg.conf.xxxx with a date near before you broke it.
If there is one, you're in luck.
```
 sudo cp xorg.conf bkup.xorg.conf 
```to backup the current one for forensic purposes, then```
sudo cp xorg.conf~ xorg.conf
```The first file(xorg.conf~) being the last good backup you found dated before it broke.
Then```
startx
```or```
sudo startx
```or```
sudo /etc/init.d/gdm restart
```I can never remember which...

If that doesn't work or you don't have a backup, you can try:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from the same login.

Thanks!

---

