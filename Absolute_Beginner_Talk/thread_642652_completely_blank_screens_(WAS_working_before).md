---
title: "completely blank screens (WAS working before)"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2007-12-16
Gutsy was running reasonably well (not as well as feisty) but I was cleaning up and must have inadvertently removed something I shouldn't have.  After rebooting, when I go into the computer by vnc and the screen is completely blank.  no taskbar, no recycle bin, no icons, nothing.  not that i know many of the hotkeys, but nothing seems to do anything.  just a white cursor on a completely blank desktop.  i plugged in a monitor and keyboard and rebooted, same thing.  

everything seems fine from a tty terminal but I can't do anything in the gui.  any suggestions?  thanks in advance

---

### Post by Nano Geek on 2007-12-17
Run this from the terminal and post the output here. ```
sudo /etc/init.d/gdm stop && startx
```

---

### Post by psykomnky on 2007-12-18
I'm having a similar problem, hopefully not too off in cause. I just installed Gutsy fresh from the CD, then the first thing I did was install the Envy package to get my ATI drivers loaded. Those finished and I restarted. When the system came back, it asked me to login, which I did, and then proceeded to load a blank screen. I can tell there are windows and stuff loaded, because the mouse changes icons when I get near an edge or something, but I can't actually see anything beyond the mouse itself.

I tried the command that was posted and received the following (this was done through SSH, obviously):
```
system:~$ sudo /etc/init.d/gdm stop && startx
 * Stopping GNOME Display Manager...                                     [ OK ]
xauth:  creating new authority file /home/dsszczuka/.serverauth.6107
xauth:  creating new authority file /home/dsszczuka/.Xauthority
xauth:  creating new authority file /home/dsszczuka/.Xauthority

X: user not authorized to run the X server, aborting.
startx
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console

```

I'm new to linux, so forgive me for any obvious ignorance regarding the above.

Also, my video card is an ATI x1950, which I've been reading mixed reviews about, so that could be part of the cause, but  I hope this is an issue that can be resolved.
Thanks.

---

### Post by Nano Geek on 2007-12-18
From what I've heard, Envy can cause problems with Linux.
You might want to try removing the Envy driver and using the open-source one that came by default and see if that fixes the problem.

---

### Post by Dropknee on 2007-12-31
This is the exact problem I have right now, I do the dpkg-reconfigure xserver-xorg but still have the problem. This problem appear when I try to uninstall the official ATI Linux 7.12 driver. I restore my xorg.conf with my backup too and no luck.

I don't want to re-install my system, is anyone know how to fix it, pls post.

---

### Post by mschoenfeld on 2007-12-31
I have a similar problem, except my fatal error says: no screens found

---

### Post by kevmore on 2007-12-31
I've got the exact same problem!!!  Loaded gutsy, updated the video drivers (ati x1950) and rebooted to a black screen which stays forever.  How do I change back to the original drivers when I can't load ubuntu? help me I'm a NOOB  and don't know much about linux.

---

### Post by Dropknee on 2007-12-31
ok my problem wasn't the official ATI driver, the problem is envy and his routine in uninstall this ATI drivers, I got all back working, I restore my xorg with my backup to be sure all working like before.

My main problem was the drivers, the dpkg-reconfigure xserver-xorg doesn't work and I dont know why, but all I do was using the ATI uninstaller from envy and restore my old xorg back. 

Be carefull with envy is you use it.

---

