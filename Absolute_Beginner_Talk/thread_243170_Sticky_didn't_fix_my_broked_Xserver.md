---
title: "Sticky didn't fix my broked Xserver"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by nerdman on 2006-08-24
This is verbatim what error I got:
> 
GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm:0.xauth -nolisten tlp vt7
Error: Command could not be executed!
Please install the X server or edit /etc/gdm/gdm.conf to point to the right place.


So I mosey on over to /etc/gdm/gdm.conf... and the thing is huge. No idea where the field to make it point is. I'm not even sure I know where the X server is installed to, really.

Please help... I didn't fiddle with it, I think. x_x

---

### Post by mssever on 2006-08-24
You definitely need an Xserver unless you want to permanently use text mode.

Try this (I'm not sure if it will work, but...)
```
sudo apt-get update
sudo apt-get install xserver-xorg xserver-xorg-core gdm
sudo /etc/init.d/gdm restart
```

---

### Post by nerdman on 2006-08-26
Well, that definitely worked somewhat. However, I now have a problem that I can somewhat recognize, but Don't really know how to fix.

"No screens found"

what I FIGURE I have to do is install the drivers for my nVidia GeForce then edit the /etc/X11/xorg.conf file to point to the right device.

..I do not remember how! I did it before... But formatting is few and far between, and I'm definitely not in a notetaking mood when my system crashes.

-What is the package name for nVidia card drivers...
-Where is the nVidia driver tutorial, I swear there was one
-If the tutorial is gone, what exactly am I editing in the xorg.conf file?

---

### Post by slimdog360 on 2006-08-26
You can install the Nvidia drivers through synaptic or aptitude or whatever. But you have to enable tem with some command which is written in synaptic. My suggestion is install from synaptic and find the command in synaptic to enable them.

---

### Post by daou on 2006-08-26
[Nvidia driver installation howto]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by nerdman on 2006-08-27
I think I could be having a serious problem because I am using Hoary Hedgehog, and all these tutorials are of Dapper release.

Can someone confirm/debunk that this could be potentially messing me up?

---

### Post by nerdman on 2006-08-27
I am still getting a "No screens found" error when my ubuntu partition boots up, the command to reinstall a working xorg.conf file does not fix the error

```

sudo dpkg-reconfigure -phigh xserver-xorg nvidia-xconfig

```

right? Didn't work.

---

### Post by az on 2006-08-27
The recent problem with xorg did not affect Hoary - you shouldn't even have gotten an update!

What broke your X in the first place?

---

### Post by nerdman on 2006-08-28
I just compulsively update. However, it broke before I had to go to the sticky.

Name off some window managers... I tried to install one of them, I forget which. it started with an 'ex', I think I remember.

I'm not comfortable enough with bash yet to just know commands off the top of my head, and I have no idea how to browse through my installed packages to find what i need to take out. I figure putting that in, with GNOME still installed broke it. (Although I sort of started to blow that off, since the updating the xserver kind of changed the problem.)

---

