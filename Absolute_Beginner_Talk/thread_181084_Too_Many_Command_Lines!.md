---
title: "Too Many Command Lines!"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by PastorEric on 2006-05-23
I have now tried twice to install Ubuntu. The 1st time I got a black screen with a command prompt in the form of eric@childrensministries. I think there was also a dollar sign in there somewhere. This time I have a very different command prompt of Grub> What am I doing wrong?

---

### Post by S{yndrom}e on 2006-05-23
I think you did a server install instead of the normal install.

Next time at the command line try doing 

startx

and see if that helps

---

### Post by nalmeth on 2006-05-23
Yes, common mistake, a lot of people do the server install, which won't give you a GUI.

if startx fail's, type

sudo apt-get update
sudo apt-get install ubuntu-desktop

You're told the xserver isn't configured properly, type:

sudo dpkg-reconfigure xserver-xorg

Pick all default's, except change the video driver to VESA

---

### Post by S{yndrom}e on 2006-05-23
or if you want a KDE envoronment do

sudo apt-get install kubuntu-desktop instead of ubuntu desktop

---

