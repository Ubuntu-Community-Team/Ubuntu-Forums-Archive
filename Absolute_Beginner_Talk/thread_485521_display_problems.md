---
title: "display problems"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Dr mac on 2007-06-27
recently i installed ubuntu in my dell note book but the window is not  comming as full screen .i ve adjusted the  resolution to the max. im totally new to linux

---

### Post by Pizzarth on 2007-06-27
do you mean that the proper resolution isn't showing up?

---

### Post by sad_iq on 2007-06-27
Have you properly installed the driver for your video card??
```
glxinfo |grep direct && glxinfo |grep vendor
```
Paste the result here!!!

---

### Post by Dr mac on 2007-06-27
ya i ve been using windows and i never had this problem so i guess the drivers are in place
what i mean is ubuntu is showing up in the middle of the screen as a small window

---

### Post by BHelts on 2007-06-27
sounds to me like you have a resolution of 800x600 when you really need 1024x768

of course these are just estimates.  Try running this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and selecting your monitor's native resolution.

---

### Post by Dr mac on 2007-06-27
my screen resolution is set to 1024 by 768

---

### Post by BHelts on 2007-06-27
on a dell, you may be able to restart the computer and hit F2 repeatedly to enter the system BIOS.  Then you want to look around (not sure where it is) and find where "LCD Expansion" is and set it to "YES".  I'm not sure this will work, but it may work.  Sounds to me like 1024x768 is not your native notebook resolution.  I had the same problem with my VAIO notebook.

---

