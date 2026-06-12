---
title: "New to Dual-Boot setup, can someone help?"
date: 2006-07-12
forum: Apple PPC Users
---

### Post by namaui on 2006-07-12
I am not new to linux but have never set up a Dual-Boot situation with Mac OS X and Linux. I am using a very old iMac. It is a Revision D machine, tray loading, 333mhz, 160MB ram and 80 GB Hard Drive split up like this:

HFS+ Macintosh HD 7.61 GB
Mixed filesystems used by Ubuntu in a 21.3 GB
HFS+ Extra OS X Partition 44.8 GB for my home folders

When re-installing OS X 10.3.9 on this machine I made 3 partitions 2 HFS+ drives and 1, 21.3 GB free space that I auto-partitioned in the Ubuntu 5.10 Installation CD with the default partitioner. It finished copying all the installation packages and restarted, but on restart I got a grey screen with the text "Can't Open" over and over again. Even Zapping the pram didnt do much. I had to reboot off the OS X install CD and select "Macintosh HD" as the boot drive in Startup Disk, then that finally did it, but i cant get back to my ubuntu boot partion which i believe is #11 for yaboot on the list. Can any provide any info as how to set up an easy dual boot setup, somewhat like grub? Just incase you dont know, even though apple has this machine listed as NewWorld, it is very similar to the beige g3 in the fact that it cant use the option key to select a boot drive at startup, or use the L or X keys to choose.

Thanks, Nick

---

### Post by namaui on 2006-07-12
As it turns out, Partition 12 is Yaboot, i believe. iPartition it says 8.50 MB, Partition #12, type: Apple Boot, name: eXternal Boot. but there is also another boot file. iPartition says 977 Kb, Partition #8, type: other/ apple bootstrap, name: untitled.

Can anyone provide any info about this, thanks again.

Nick

---

### Post by AlphaMack on 2006-07-12
What you need to do is repartition your Mac.

Unless for some reason you need multiple partitions of different OS X installs, I would only set up 3:  one for OS X, one for Ubuntu, and one for your data to be shared between the two.

First, put in your OS X install CD/DVD and open Disk Utility from there.  Completely wipe the drive and zero all data.  Then set up the three partitions:

First partition should be OS X and marked as HFS+ journaled.  OS X requires as little as 8 GB but first calculate how much your /Applications are taking up.  I personally set aside 35 GB for my setup.
Second partition should be for Ubuntu and marked as free space.  8 GB should be sufficient (6 GB for / and 2 GB for /home).  That is assuming you have a LOT of programs.
Third partition should be for your data.  You can mark it as HFS+ so as long as it isn't journaled.

Install OS X first.  When done, stick in the Ubuntu CD and have the partitioner automagically partition the free space.  I would recommend that you use the alternate CD to do this because you can go back and split the / partition to create another one solely for /home (then this way if you bork your install your /home data is safe).

HTH

---

