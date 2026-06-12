---
title: "New to Linux"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by mrbadnback on 2007-04-04
I just downloaded and installed Ubuntu on a CD. I want to install it on my system but I don't want to reformat and install everything again. Can I install it on my RAID0 without reformatting and partitioning first? I want to dual boot it with my XP but I want to make sure that I can partition the hard drive and install it without going through reformatting. Plus I have used Windows all my life and really want a change but I know nothing about Linux and how everything is supposed to be done. I don't really know anything about DOS either. LOL

---

### Post by oilchangeguy on 2007-04-04
just take it for a test drive first. boot from the live cd and run it that way until you are ready to install it.

---

### Post by mrbadnback on 2007-04-04
Since it will be on the CD will I be able to install different things I need. I have run it on CD yesterday but noticed that I can't do certain things like update or even install things. So that is why I was asking about installing it.

---

### Post by Bachstelze on 2007-04-04
Yes, you can install (most) software on a Live system to test it out but it will be lost when you'll reboot.

---

### Post by mrbadnback on 2007-04-04
I noticed that yesterday. I turn my systems off at night so I will lose everything that I get done. 
 Since I have 2 Sata drives configured into Raid0 with no partitions can I still install Ubuntu from the desktop of the live CD? Will it partition my hard drives and install Ubuntu without me having to reformat my HD's and partitioning and installing that way? Plus will it interfere with the XP and its drivers?

---

### Post by Patrick K on 2007-04-04
AFAIK, you will need to format a partition for Linux. Again, AFAIK, it will not run, or install, to NTFS or Fat32. It has to have a compatible file system, of which there are several. EXT3 is the default for Ubuntu. 

When you format a partition for Ubuntu, it will leave the other partitions alone, except that it will install the GRUB boot loader to provide dual booting to Linux and whatever other OS's you have on the system. It will not interfere with XP or its drivers.

---

### Post by mrbadnback on 2007-04-04
Thanks for the help. I guess I will wait until I reinstall my OS before I install Ubuntu since It can't be done any other way.

---

