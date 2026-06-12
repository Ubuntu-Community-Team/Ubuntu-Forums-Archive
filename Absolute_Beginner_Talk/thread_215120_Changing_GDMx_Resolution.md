---
title: "Changing GDM/x Resolution"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Moldy Peaches on 2006-07-13
Hi, I just installed Ubuntu 6.06 in VirtualPC.  Everything went smooth, but I think I messed up the resolution somehow.  When I first boot into GDM, I get a resolution that is too high for my screen and a very distorted looking picture.  Additionaly, the colors are all messed up, but I am aware this is an issue with x's default color depth and vpc.

What is the  best way to change the resolution of GDM and X?  As it is, I can barely make out the pictures on the login screen.

thanks

---

### Post by Paerez on 2006-07-13
press ctrl+alt+f1 to get to a nice happy terminal and log in. Then run:
```
# sudo dpkg-reconfigure -phigh xserver-xorg
```
you can hit enter for anything you are unsure of (if you hit enter all the way through that is the default dapper settings). At one point, it asks what resoultions you want, and you can put an X next to the ones you want.

---

### Post by dbw on 2006-07-15
(& sudo dpkg-reconfigure gdm) ;)

---

