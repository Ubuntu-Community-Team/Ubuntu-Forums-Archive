---
title: "gparted broke ubuntu"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by gutsy goober on 2008-01-19
My computer is a sony laptop that currently runs windows vista.  I used vista's partition manager to create unallocated space.  Then booted into ubuntu livecd and created an extended partition with gparted to install ubuntu, and when I clicked "apply", it seemed to work ok, then gave me an error (which I stupidly did not write down).  I tried to reboot with the ubuntu livecd and the initial menu worked ok, but after trying to start ubuntu I got a screen with a couple lines on it and nothing else.  I went back to vista's partition manager, which recognized the new partitions as "healthy", but removed them back to unallocated space anyway.  Rebooted ubuntu and still just got the funny lines on the screen.  Any ideas?

---

### Post by ajgreeny on 2008-01-19
Sounds like graphic card problem, though why it worked first time seems a bit of a mystery.  What hardware have you got in the machine?  It could be worth trying again using the low graphics boot (I can't remember exactly what the option at boot time is called, but that is basically it) which may at least give you a GUI from which you can then do things to put the display right.

---

### Post by gutsy goober on 2008-01-19
I tried this but still got the same sort of non-images on the screen.  I have to admit I have absolutely no idea what to do, outside of trying a different distro.

---

### Post by louieb on 2008-01-19
Check the CD.  Choose  the check media for defects option. IF there are errors you'll need to burn it again. I recommend   burning and 4x or 2x.

---

### Post by gutsy goober on 2008-01-19
Yeah, I've already done the check cd for errors, and performed a checksum on the iso image file, and both came up ok..  the livecd worked fine before I tried to repartition.  I'm really confused.

---

### Post by louieb on 2008-01-19
Since the CD is probably good: It really weird that the Live CD worked before but not after using GParted.  
Might try the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and run Gparted again a write down any error it gives you. or 

  As ajgreeny says it time to play with boot options. Not much help but heres a couple of lists. Try a few options that alter how video is used.
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")  Knoppix like Ubuntu is based on Debian Linux - most of these apply. 

You just might try a Knoppix Live CD. Its one of the best around for hardware detection.

---

### Post by gutsy goober on 2008-01-20
Thanks for the reply.. turns out I got ubuntu installed by using an amd64 livecd I had to do the partitioning, then installing the i386.  I'm not even going to try to figure out why this worked.

---

