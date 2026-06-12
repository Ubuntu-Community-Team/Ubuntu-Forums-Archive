---
title: "How should I format my hard drive partitions"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2006-10-27
I was reading in the Ubuntu blog that it's a good idea to have four paritions for ubuntu.

[https://features.launchpad.net/distros/ubuntu/+spec/better-installer-settings](https://features.launchpad.net/distros/ubuntu/+spec/better-installer-settings)

Quote from above site:

/hda1 around 32mb /boot partition. Usually ext2
/hda2 2 X how ever much ram I have Linux-Swap
/hda3 around 10-15 gigs root partition.
/hda4 Whatever is left for /home.

If I wanted to dual boot with Windows XP, should I have
1) boot partition
2) Linux swap drive
3) Root parition for Linux
4) Partition for Windows
5) Partition for Personal Files

How should I format the drives if I wanted to be able to access the Personal Files partition from both Windows and Linux.

Thanks in advance.  I'm guessing it's going to be FAT32.

I don't really know any advantages or disadvantages to the different formats.

---

### Post by bodhi.zazen on 2006-10-27
for a shared drive use either ext2 or FAT.

for basic partitioning: [Basic partitioning](http://ubuntuforums.org/showthread.php?t=282018)

[ext2 on windows](http://www.fs-driver.org/index.html)

---

### Post by bulldog on 2006-10-27
Hi,well to begin I should make only three partitions.

Make a 10GB / (root) partition.
If you have 1024MB RAM make a 1024MB swap bigger is no need for.
The rest of the space for Ubuntu you make /home your user partition.

To read and write files between windows and ubuntu,create a fat32 partition.


Hi Bodhi,still around doing the good work?

---

### Post by bodhi.zazen on 2006-10-27
> **bulldog said:**
> Hi,well to begin I should make only three partitions.

Make a 10GB / (root) partition.
If you have 1024MB RAM make a 1024MB swap bigger is no need for.
The rest of the space for Ubuntu you make /home your user partition.

To read and write files between windows and ubuntu,create a fat32 partition.


Hi Bodhi,still around doing the good work?

Bulldog: Long time no see.  I'm trying the best I can :)

I've been working on partitioning and fstab as these questions seem to come up often.

work-work has been busy.

ski season is almost here !!

---

### Post by xpod on 2006-10-27
:-#

---

### Post by bulldog on 2006-10-27
> **xpod said:**
> :-#
Well well,xpod himself comes around.

All in good shape xpod?
Computers all working out with your private technician?

---

### Post by bodhi.zazen on 2006-10-27
All paths lead to.....
[indent]xpod[/indent]

---

### Post by xpod on 2006-10-27
Pc`s are all fine, os`s all seem to work and the desktops are on fire so im as happy as a pig in s**t:D 

The technicians got a big muckle lump on her noggin......she`s up and walking now and getting just a wee bit too brave for her own good](*,) 

All good though......

Welcome to the machine JR.....this pair will have you up and running in no time m8:D 

Great os,great forums and a whole load o great people making it happen..
Good stuff!!!

EDIT..i got me more kernals than a squirrel in winter;)

---

### Post by louieb on 2006-10-27
In my computer playground I have 1 XP box, 1 Box that dual boots XP and Ubuntu, 1 Box that  boot half a dozen Linux distributions and an old P1 200 that currently  runs Slackware Linux.

I am A+ certified and have been playing with computers since before the days of DOS.

If your just starting out with Linux the then I suggest KISS. Unless you know how you are going to use the PC it is impossible to say.

For example if you are going to boot just one Linux distribution I would just use the installation defaults.

If your going to set up dual boot XP and Linux the need for a fat32 data partition would depend on which operating system you spend the most time in. 
I spend most of my computer time using Ubuntu on the machine that dual boot to XP. XP is in an NTFS partition and Ubuntu is in an EXT3 partition. I don't have a need to write to the XP partition from Linux. There are free programs on the Internet that allow XP to read and write to EXT3/EXT2 partitions as if they were just another windows drive. Linux has no trouble reading NTFS but writing is a little iffy.   

Four months ago I installed Linux for the first time.  I was paranoid about loosing all the stuff I had on XP. So I got a second hard drive and installed Linux on it.  One of the better moves I have made lately.

Ok back to KISS and dual boot XP and Linux on a single drive.
3 Partitions.
Linux swap (double your memory size 1 gig max).
Windows and Linux get the other two just split the remaining disk space between them.  
Format the Linux partition EXT3. Format the XP partition NTFS unless your really feel the the need to write to it from Linux in that case format it FAT32.

I've rambled on enough. I hope I have confused you enough to just try Linux. Do you know that when Tomas Edison was trying to make a light bulb he tried 10,000 ways that did not work before he found the one that made the light bulb possible.

---

### Post by wieman01 on 2006-10-27
> **bodhi.zazen said:**
> All paths lead to.....
[indent]xpod[/indent]
Eventually, eventually... :-)

---

