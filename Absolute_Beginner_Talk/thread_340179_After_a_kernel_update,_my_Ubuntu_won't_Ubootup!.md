---
title: "After a kernel update, my Ubuntu won't Ubootup!"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by je1117 on 2007-01-16
Ok, first of all, I love Ubuntu. So much that I refuse to give up this time.

Ok, so I can get it up and running just fine. The installation, for the most part, was a breeze. So when I first boot up, I choose the 2.6.15-23-amd64-generic, as it's my new Ubuntu kernal blah blah. I can boot up fine, but the video is obviously not optimum. So I installed the build-essential files, downloaded the ATI Linux Proprietary driver.run. (i'm running a Radeon 9200.) I compile and install the drivers - they work fine.

This driver works fine with the 2.6.15-23 kernal. But when I download the 211 or 215 someodd updates, it updates the kernal to 2.6.15-27. Now at the bootup I can choose between the 23 and the 27 kernel. BUT IT DOESN'T MATTER BECAUSE NEITHER BOOT. I've tried both recovery modes, and when I enter any key strokes at the command prompt it gives me error after error. I can't even get to a login screen. My monitor just goes into standby, no sound.

I've looked and looked with someone with my problem, and alot seem SIMILAR, but nothing too spot on.

So I suppose my question is, WHAT AM I DOING WRONG? haha. Should I just not upgrade to the newest kernel? Or should I give up and get a new video card? (don't really want to...)

HELP!!!

---

### Post by je1117 on 2007-01-16
are the drivers in easyubuntu the same ATI drivers as the proprietary ones off the ATI website?

---

### Post by riven0 on 2007-01-16
Okay, try booting into recovery mode. If it doesn't automatically put you into root mode, do this: **sudo -s -H**

Now try re-installing the kernel image headers:

> apt-get install kernel-image-2.6.15-27-amd64-generic; apt-get install kernel-image-2.6.15-23-amd64-generic

Then reboot and see if you can get in.


EDIT: Yes, the easyUbuntu ATI drivers are the official ones. Ubuntu comes installed with the open source drivers, which are reversed engineered and unofficial.

---

### Post by je1117 on 2007-01-17
how can i tell if i installed the drivers correctly? i used easyubuntu and am getting the same performance. no 3d acceleration.

---

### Post by riven0 on 2007-01-17
Do **fglrxinfo** to determine whether you have the ATI drivers installed. If you see something like OpenGL or Mesa, the drivers are *not* installed.

---

### Post by je1117 on 2007-01-17
riven, it gives me "Error: couldn't find RGB GLX visual!"

---

