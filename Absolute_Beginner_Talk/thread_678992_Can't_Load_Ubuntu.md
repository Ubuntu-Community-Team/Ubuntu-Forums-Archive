---
title: "Can't Load Ubuntu"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by ghoss00 on 2008-01-26
Can't get Linux to load.  After the initial screen, monitor goes black and system hangs.   Equipment:   DFI motherboard with a socket 939 AMD dual core CPU, 4 GB Ram and a reserved primary petition of about 90 GB reserved for Linux.  My video board is ATI Radeon X700 Pro (PCI Express).  Any ideas?

---

### Post by Presto123 on 2008-01-26
Try running it by selecting "Safe Graphics" in the install menu. Or have you already installed it?

---

### Post by ghoss00 on 2008-01-26
Tried loading in safe mode, but no go.  Won't install.

---

### Post by Jelmoh on 2008-01-26
Did you already run the 'test cd' (also in that install menu)
If it says the CD is corrupted burn on lower speed... :)
I had the same problem, also you could try to use the i386 version (except for when you are certain you've got a 64-bits CPU)

---

### Post by dstew on 2008-01-26
> Can't get Linux to load. After the initial screen, monitor goes black and system hangs.Are you referring to the Live CD, or to an installed hard-disk Ubuntu system?

---

### Post by ghoss00 on 2008-01-26
I downloaded the UBUNTU Iso & their recommended CD Burning program.  I burned the CD at lowest speed.  I am trying to install from the CD and not from any hard drive.  My motherboard is an AMD socket 939.  I installed an AMD Athlon 64 dual core.  I run Windows XP64 PRO in the first Petition, Windows XP Pro (32bit) in the second Petition and am trying to load Ubuntu Linux in the third.  In addition I am running two RAID clusters, and a secondary hard drive.

---

### Post by ghoss00 on 2008-01-26
I did run the "Test CD" in the install window, but got the same result.  If that proves the CD to be defective, I'm not sure what to try next since I used Ubuntu's iso and recommended cd burn software at the lowest speed.  Not sure what needs to be different.

---

### Post by uxe1 on 2008-01-26
come times theres a defect on the cd its self. 
also i had a similer problem with gutsy when i was using my ati card and a lcd monitor. but when i tried on my old crt monitor  it worked, i haven't tried to hook up my lcd again because   its on a different computer now

---

### Post by dstew on 2008-01-26
There are many ways a Live CD can fail to work. The Live CD system is limited in the kind of hardware it can run on. It might be having a problem with your ATI display adapter, for example. But it can be other things, like the advanced programmable interrupt controller, or your power control hardware. You can try to get the Live CD to run using kernel parameters, entered using F6 from the initial screen, but that is trial and error.

My advice: download and burn the Alternate Install CD. It installs the same Ubuntu system as the Live CD, but uses a simpler text interface so it will run well on any computer. After you have Ubuntu installed, if you have any issues getting it to run, we can work on them later. You get the Alternate Install CD from the [Ubuntu Download page]("http://www.ubuntu.com/getubuntu/download"), just check the box below the Start Download button.

---

### Post by ynef on 2008-01-26
> **ghoss00 said:**
> I did run the "Test CD" in the install window, but got the same result.  If that proves the CD to be defective, I'm not sure what to try next since I used Ubuntu's iso and recommended cd burn software at the lowest speed.  Not sure what needs to be different.

I honestly don't think this is the problem, but did you check that your download was correct using the MD5 sum? They say (IIRC) that it is something only advanced users need to worry about, but that is just plain wrong. I must've tried downloading the ISO five times on one particular computer before it downloaded correctly.

---

### Post by ghoss00 on 2008-01-27
> **dstew said:**
> There are many ways a Live CD can fail to work. The Live CD system is limited in the kind of hardware it can run on. It might be having a problem with your ATI display adapter, for example. But it can be other things, like the advanced programmable interrupt controller, or your power control hardware. You can try to get the Live CD to run using kernel parameters, entered using F6 from the initial screen, but that is trial and error.

My advice: download and burn the Alternate Install CD. It installs the same Ubuntu system as the Live CD, but uses a simpler text interface so it will run well on any computer. After you have Ubuntu installed, if you have any issues getting it to run, we can work on them later. You get the Alternate Install CD from the [Ubuntu Download page]("http://www.ubuntu.com/getubuntu/download"), just check the box below the Start Download button.
I have now downloaded the alternative ISO for AMD64 and installed.  Everything seemed to go well until it came to first boot.  Just after the first menu, the screen text said something like " the kernel in alive" then the srceen with black followed by the monitor light going out.  So I next booted using the "safe mode" (the second choice, I believe) and saw lots of text flying by the screen.  Finally the screen halted for input from me.  root@glen:~# where glen is the computer name.  I have been going through the "Ubuntu Linux Bible" but can't seem to find the proper command line answer.  Any ideas?

---

