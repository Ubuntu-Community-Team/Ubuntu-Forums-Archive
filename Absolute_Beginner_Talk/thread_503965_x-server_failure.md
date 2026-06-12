---
title: "x-server failure"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by keese on 2007-07-18
I know that there are a lot of other people who have had this problem, but it might take a little doing to get me through this mess.  Anyway, to start I guess I should tell you guys that I'm a noob.

A year ago I tried to install Ubuntu onto my PC, but the error message saying that X-Server kept me from being able or willing to completing the install.  Now there is a software called Wubi, which is basically a way of installing Ubuntu with Windows still running.  It worked, there were no problems with wubi, but I still got the error message:
"Failed to start X Server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the x server output to diagnose the problem?"

Now I guess I should tell you what I've tried:
   I've tried to reinstall x server with "sudo apt-get install xserver /etc/X11/"  It said that x server was already installed.
   I've tried "sudo dpkg-reconfigure-xorg"  It said something about it not being a known command
   Lastly I've tried "/etc/X11/xorg.conf" to try to change the driver to "vesa".  When I typed that in it spat out the same unknown command thing.

---

### Post by CautionaryX on 2007-07-18
Hi, 

Could you tell us some information about your hardware (esp. videocard)? 
Also, which version of Ubuntu are you trying to install?

BTW, the proper command is:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by keese on 2007-07-25
yea sure.  my video card is a nvidia GeForce 5500 with 256MB of VRAM, which seems to be recongnozed automatically (dont have to mess with plugs).  I have a Intel Pentium 4 Processor 2.8 GHz, 512 RAM, a CD-R drive and a DVD-RW (not working), and a 160GB HDD. Hope this helps.
Oh and I'm trying to install ver. 7.04

---

