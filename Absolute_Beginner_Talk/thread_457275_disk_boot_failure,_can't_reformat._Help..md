---
title: "disk boot failure, can't reformat. Help."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by frankeleone on 2007-05-28
Hello,
	I have really screwed up. I'm not sure what info is important, so here is what I have. I was running Kubuntu feisty on x86 machine. I was trying to get my ipod mounted and the only way it was mounting was to plug it in and restart the computer. After doing things that I can't remember in root, I restarted the computer and got this message: Disk boot failure, insert system disk and press enter. Ok, big problem; I figure that I have to reformat and start from scratch. So, I put in a feisty installation DVD. I try to install. First, I try to do an automatic partition and it says it will use the whole disk. I start that and get an error : Creation of swap space in partition #5 of SCSI1 (0,0,0)(sda) failed. I then try to do a manual partition, and under the dialog box that says Prepare partitions, it only lists the device /dev/sda. When I try to create new partitions, it gives me the same error (creation of swap space in...failed). In desparation, I shut the computer down and tried to load windows xp. At some point it stops me and says that it cannot access any hard drive. I don't think the hard drive has exploded as when I tried to reinstall Kubuntu, it can read that I have 20gb of space, which is my hard drive size. I am lost as to what to try other than to give it to a repair guy, which I am unlikely to do as I bought this computer for less than it will cost to diagnose and repair the problem. I am still able to use a live cd, which is how I am communicating now. Please help. As you can guess, I am a newbie of sorts, although I have been using Kubuntu for the past year or so. I know, never mess in root again...Thanks, Frank

---

### Post by Happy_Man on 2007-05-28
No offense to you or anything, but this is why Ubuntu locks root. :D

Why won't it let you create swap? Have you tried manually partitioning?

---

### Post by coderK on 2007-05-28
Try the Testdisk Utility which came as a life saver to me. It might just work. Anyways, you can run it on the liveCD. Let us know if its any help.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

