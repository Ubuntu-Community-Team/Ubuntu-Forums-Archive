---
title: "Failed to start x server"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by karishbhr on 2007-04-29
I get this error when i turn on my pc now, ubuntu 7.04. I am not sure what I did to get this error but can someone post some solutions, i already reinstalled gnome, and tried to reconfigure the xconf file thingy.

when i goto diagnose it says "please install the xserver or correct gdm configuration and restart gdm"

---

### Post by nanotube on 2007-04-29
> **karishbhr said:**
> I get this error when i turn on my pc now, ubuntu 7.04. I am not sure what I did to get this error but can someone post some solutions, i already reinstalled gnome, and tried to reconfigure the xconf file thingy.

when i goto diagnose it says "please install the xserver or correct gdm configuration and restart gdm"

just to be sure, you already tried using
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
?

---

### Post by karishbhr on 2007-04-29
i did and the problem remains.

here is what it says when i goto the diagnostic:

GDM: Xserver not found: /usr/bin/xgl  :0 :0 -fullscreen -ax -accel
glx:pbuffer  -accel xv:fbo -auth /var/lib/gdm/ :0.xauth -nolisten tcp vt7
error: command could not be executed!
Please install the x server or correct gdm configuration and restart gdm

---

### Post by zetsumei on 2007-04-29
Did you do anything major or the xorg.conf file before or is this the first time running Ubuntu?  If it's the latter, ALWAYS make sure you backup your xorg.conf file in case it breaks.  Last night alone, I had my X server crash like 10 times trying to get the nvidia drivers working LOL

---

### Post by Gusse on 2007-04-30
I don't think this is the xorg, because I have the exact same problem, see my [thread]("http://ubuntuforums.org/showthread.php?t=427153"). I first installed the driver and compiz, which didn't work, and when I tried to revert the changes I still got that error. The system works fine actually, I just have to log on after I get the error, and then *startx*. Then gnome starts up and everything seems to be ok. I looked at the */etc/gdm/gdm.conf-custom* file I had edited, and noticed that I hadn't been successfull in reverting my changes (in the [servers] paragraph). I took away everything, which made the xserver error go away, but unfortunately I then couldn't get anything more than the black/white mesh and the mouse, the "human" color never comes on boot and it seems the computer freezes. The last days I've been using the machine by logging in after the error and then manually starting the xserver. I really wish someone could tell me how I could remove the packages and get the .conf files straight.

Gus

---

