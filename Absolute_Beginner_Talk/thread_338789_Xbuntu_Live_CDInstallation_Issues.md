---
title: "Xbuntu Live CD/Installation Issues"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Real Newbie on 2007-01-14
All,
I downloaded the iso for the 6.06 LTS CD and have been fooling with it. I have a couple of problems. The biggest at the moment is that the screen resolution is so large that I can't do an install. I followed the instructions that I found on another thread "press ctrl-alt-F1 to jump into command line" it logs in and it walks you through configuring your system. At the end I am stuck at the command line. If I pres ctrl-alt-F7 it takes me back to my screen however, the resolution is still horrible. I can't do the install as I can't get to the bottom of the windows to click the config buttons.

Help! What do I do?

Real Noob

---

### Post by rccharles on 2007-01-15
> **Real Newbie said:**
> All,
I downloaded the iso for the 6.06 LTS CD and have been fooling with it. I have a couple of problems. The biggest at the moment is that the screen resolution is so large that I can't do an install. I followed the instructions that I found on another thread "press ctrl-alt-F1 to jump into command line" it logs in and it walks you through configuring your system. At the end I am stuck at the command line. If I pres ctrl-alt-F7 it takes me back to my screen however, the resolution is still horrible. I can't do the install as I can't get to the bottom of the windows to click the config buttons.

Help! What do I do?

Real Noob

Did you get your system installed?  Try re-booting without the cd in the drive.

If you have installed Ubuntu, you need to edit the file xorg.conf to a working screen size.
While I am not an expert on xorg.conf, you need to edit this file and delete out the Modees you do not want.  

Try:

get a backup copy
cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo nano /etc/X11/xorg.conf

See the sections SubSection "Display"

delete the Modes you do not want.

save the file

Reboot now or enter the following commands.

sudo init 1
sudo init 2

Robert


...

When installed a fresh Ubuntu, you can change the screen size.  When you get the Ubuntu logo, press f4.  Select the screen size you wish.

Robert

---

### Post by meng on 2007-01-15
Try installing with the Alternate CD. This installer is text-based not graphical, but is just as easy to use. After installation, you may require some post-install configuration, but it should be easier than messing around with the Live CD.

---

### Post by Real Newbie on 2007-01-15
I think the best idea is installing the alt iso. I have tried 3 times and failed each time. I think that the issues is I am trying to do a dual boot. I erased all the partitions and am now trying the 4th time.

I will let all know how it goes.

Thx for the help.

---

### Post by Real Newbie on 2007-01-15
All,
Thanks for the suggestions. I cleared out all of the partitions and reinstalled and it worked great. I had a few hairy moments getting the resolution correct, but that is OK for the most part. I am working on the wireless now. I just started a new thread.

For what it is worth, Xbuntu is pretty impressive on this old laptop. It is still a little slow, bit not unacceptably so. The desktop looks great


Thx for the help

---

