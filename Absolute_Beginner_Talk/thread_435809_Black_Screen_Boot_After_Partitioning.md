---
title: "Black Screen Boot After Partitioning"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by LE CHARBON on 2007-05-07
I used gparted to move my partitions around. Gparted asked about my video drivers, it said it could not load the gui. I told it force a VGA driver and it worked. Anyway, everything went fine. I rebooted into UBUNTU 7.04 with no problems, everything is great. I then booted windows, everything fine. Then, windows says it installed new hardware and I must reboot. I did that and now UBUNTU boots to a black screen. Ubuntu looks like it is loading but I can not see it. Did windows or myself screw up the video drivers? Is there a fix to this? Can someone give an answer? I am completely new to this.:confused:

---

### Post by Seisen on 2007-05-07
Do you have a regular graphics card or is it an nvidia or ati card? Sounds to me like X got messed up somehow.

---

### Post by LE CHARBON on 2007-05-07
Regular. I have a Dell Flat screen, nothing fancy at all.

---

### Post by hellblade on 2007-05-07
After booting ubuntu press alt-ctrl-F1. This should switch you to a login shell (no graphics). Login with your username and password and after backing up your X configuration file, reconfigure your X server.

**Details:**
1. switch to login shell (Alt-Ctrl-F1) and log in.
2. go where your X configuration file is
```
cd /etc/X11
```
3. back it up
```
sudo cp xorg.conf xorg.conf.old
```
4. reconfigure X and select your VGA driver when asked
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If you don't know which card you have try this and paste the output here.
```
lspci | grep VGA
```

These assume that the problem lies in X not being able to start. If your problem is elsewhere, they want help.
Also can you somehow post your "/var/log/Xorg.0.log"? If you can't copy this file because you don't have a GUI try [explore2fs]("http://www.chrysocome.net/explore2fs") for windows. It's perfectly safe (read only access).

---

### Post by LE CHARBON on 2007-05-07
This is probably an obvious question, but can i find out the driver type on windows side? And where would that be?

---

### Post by hellblade on 2007-05-07
Do you know what VGA card you have? Nvidia, ATI etc
In windows you can check that by right click on desktop > properties > advanced
Not sure if these are the right steps but it's in the same place with the resolution options. There should be something like "Your_Monitor on Nvidia Geforce 7600"

---

