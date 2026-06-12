---
title: "Ubuntu/XP dual boot erases XP"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by johnnyloot on 2006-12-21
Hey Guys,
I just got a new computer and I am trying to dual boot XP and Ubuntu (6.06 for now). 
After getting XP installed and running I am trying to install Dapper so I can dual boot.

Problem is that I have now twice messed up and when I try to boot I get a "error loading operating system" error. 

I made sure to defrag my HD and there is plenty of space (120GB of which only 5 are used).

When I use the partition tool in the ubuntu installer, the first time I made a 20GB partition and a 1 G swap at the end of the drive (to try to avoid any issues), but that did not seem to work.

The next time I tried to use the tool which asks you what percentage of the drive you want to take up. 20% sounded good, so I tried that.

Same problem.

Can anyone help me here?

---

### Post by dbbolton on 2006-12-21
when you say "did not seem to work", what happened, exactly ?

---

### Post by johnnyloot on 2006-12-21
gave me the "error loading the operating system" error

on both occasions

---

### Post by dbbolton on 2006-12-21
is XP already installed on (hd0,0), or whatever the first partition is called ?

---

### Post by atarileaf on 2006-12-21
I too had a similar problem and couldn't get around it so I simply used a second hard drive for Ubuntu. If you have a second hard drive kicking around (at least 10 gig I would think), then you should be all set. When the install asks, simply choose your second drive and away you go. GRUB will be installed to your MBR on your first drive.

I find its a much better solution to partitioning one drive for both OS's and since most everyone has old drives kicking around, its a perfect solution.

---

### Post by gn2 on 2006-12-21
If you have a Windows CD insert it, and re-start.

Select Recovery mode and run the command "fixmbr"

This will restore the Windows native bootloader.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

If you can add a second hard drive this may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by bodhi.zazen on 2006-12-21
> **johnnyloot said:**
> Ubuntu/XP dual boot erases XP

That sounds more like **problem solved** to me :mrgreen:

For help installing Ubuntu:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by moshuptrail on 2006-12-21
When you create the Linux partition be sure to format the partition.  If it comes back real fast (like I can't believe you formatted the drive THAT fast)  then use the Gparted Live CD.  I had a lot of problems with the installer sort of skipping the format step.  Then wierd things would happen - the worst of which was the installer crashing.

---

### Post by Sef on 2006-12-21
From the terminal (Applications > Accessories > Terminal):

sudo fdisk -l

then copy and post the results here.

---

