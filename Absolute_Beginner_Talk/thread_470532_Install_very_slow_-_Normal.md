---
title: "Install very slow - Normal?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by resander on 2007-06-11
I have downloaded 7.04. MD5 checksum was OK.
Burned CD using Nero and for a second attempt using InfraRecorder.

Both CDs passed CD check on initial boot on target system.

Both attempts to install got to a point where the install program displayed
a list of loading so and so, starting so and so with the last being
 'Starting the printing system cups'.
After that
the screen went blank for about 10 minutes and then an outlined X
appeared smack in the middle of the screen. It was there for about
20 minutes and was replaced by a small circle with arrows
moving round and round in it. That disappeared after a couple of
minutes. The CD drive indicator light shows that information is
read from the CD. I abandoned after about 90 minutes and I am
now yet again staring at the blank screen using the CD burnt by
 InfraRecorder.

The install seems ultra slow.

Is this the way it is? Then how long will it take for the initial install dialog to pop up?

Help - a cry from an old MSDOSer and Windowser...

---

### Post by darren1270 on 2007-06-11
Please provide your system specs... Processor, Ram, Hard Drive.... My setup took about 25-30 Minutes start to finish.... I have Ubuntu installed on two systems a compaq presario with almost a gig of ram and also a duel boot toshiba laptop....

Darren

---

### Post by ramjet_1953 on 2007-06-11
No, this is not normal.

It sounds like we have a harware issue here.

Quite often this is overcome by downloading the alternate CD and using that.

The alternate CD does not have a graphical installer and often succeeds, where the Live CD fails.

I know it's probably a pain to download another CD, but it's worth a try.

By the way, even though the alternate CD doesn't have a graphical installer, it is very intuitive and you shouldn't have any problems with it.

If you do still have problems, don't hesitate to come back to this forum and seek assistance.

Regards,
Roger :cool:

---

### Post by resander on 2007-06-11
Thanks!

System spec:  Pentium III (750MHz), 256MB, set up as dual boot. Windows XP runs on one partition, so Linux should have no problems with that.

I will download the alternative distribution and will feed back outcome to the forum.

Breaking news:  my second attempt is still running on another PC. An arrow cursor just spontaneously parked itself against a light yellow background canvas but does not move with the mouse. Didn't last long, screen is back to blank again.

---

### Post by dptxp on 2007-06-11
> **resander said:**
> Thanks!

System spec:  Pentium III (750MHz), 256MB, set up as dual boot. Windows XP runs on one partition, so Linux should have no problems with that.

I will download the alternative distribution and will feed back outcome to the forum.

Breaking news:  my second attempt is still running on another PC. An arrow cursor just spontaneously parked itself against a light yellow background canvas but does not move with the mouse. Didn't last long, screen is back to blank again.

Your RAM is low.
Why not make a SWAP partition of 2 GB at the end of the harddisk using GParted first ?
I succeded that way. You shall not be able to remove SWAP partition during installation
using Live CD. But then, keep it, you need a SWAP.

---

### Post by ramjet_1953 on 2007-06-11
Yes, your RAM is very low for a GUI.

Under windows, it must have been struggling.

Any GUI needs some elbow room.

For a proper feel of Linux with GNOME, or KDE at least 512 Meg is required.

Regards,
Roger :cool:

---

### Post by mocqueanh on 2007-06-11
You will want Xubuntu:

[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by sturat on 2007-06-11
i've been having a similar problem getting ubuntu to install on my ps3. it's my understanding that it also only has 256 megs of ram in it. it is painful slow from the live cd install. i will try a non-graphical install later today when i get home.

the other systems i have installed ubuntu on, however was very swift, and moderately painless, with the exception of officially unsupported drivers.

the swap space will definately help. the formatting options from within the ps3 os is fairly limited, but iäll try to install a swap space on the partition that ps3 made before i try to reinstall with graphical interface. if i can avoid downloading another cd, i will :D

---

### Post by dptxp on 2007-06-11
> **ramjet_1953 said:**
> Yes, your RAM is very low for a GUI.

Under windows, it must have been struggling.

Any GUI needs some elbow room.

For a proper feel of Linux with GNOME, or KDE at least 512 Meg is required.

Regards,
Roger :cool:

256 MB is fine for XP, till you run some antivirus stuff. I dual boot on my Sempron 2500+ desktop, 256 MB RAM (64 MB from it goes to Video Ram). And I am using Gnome. Had to make SWAP first to install with Live CD. Gnome runs fine, but XFCE may run much faster. KDE is no longer the light weight stuff it used to be.

---

### Post by lazyart on 2007-06-11
You can get the alternate CD which is text based but will install a lot quicker.

---

