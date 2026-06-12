---
title: "Partition and HDD space problem"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Commando on 2008-01-19
First of all, hello everybody.
I want to notice that I have the ubuntu 2 days, so I am still a total n00b =).
Here's my problem: When I was installing the ubuntu on my PC, I made a partition manualy, one big 10GB. Now, when I browse the files in "Computer", it shows like my HDD is big only 10GB, and I cant see any of the files that I have. I have two questions:
1. Is it possible to access those files?
2. If not, I will have to re-install the ubuntu, but how to make the whole HDD avalible, without formating my documents?
Thanks, bye :).

---

### Post by jken146 on 2008-01-19
Please open a terminal (Applications > Accessories > Terminal) and post the output of ```
sudo fdisk -l
```

---

### Post by Commando on 2008-01-19
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x827c827c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux


Ok, it can see the whole HDD, but still I cant access my files.
Any suggestions?

---

### Post by jken146 on 2008-01-19
You have one partition on your disk.  The rest seems to be just free space.  If you want to create a partition in the rest of the space, I suggest you use gparted.

First, install it:
```
sudo aptitude install gparted
```
Then run it:
```
gksudo gparted
```
All you need to do is create a new partition in the whole of the remaining space on your disk, which is called **hda**.  Format it as **ext3**.

---

### Post by Locutux on 2008-01-19
This looks like you formated your previous partitions. :S

---

### Post by Commando on 2008-01-19
If I make that partition, will it delete the rest of my files?
Or they are formated already? :S

---

### Post by ajgreeny on 2008-01-19
You have no swap partition, which is not a good idea, and I think it would possibly be a situation where to reinstall may be best; if nothing else it will get you used to installing a linux distro, and you will find it all gets easier with repetition.  I presume you only have this one disk as that is all that shows in the fdisk output, but if you have others we need to know.  Also need to know why you are using such a small part of the disk when you have 250GB available.  There appears to be nothing other than an ext3 partition, so no Windows.

---

### Post by Commando on 2008-01-19
I am using so small part of the disc, because that is the partition that i made when installing the Ubuntu, 10GB. Still, I cant say for sure if my files are deleted or not, because it keeps showing that I have only 6-7 GB free space (thats what has left from the partition space). The partition is ext2 I guess, thats what i chose when I was installing.
I'll ask again: Is there a way to re-install the Ubuntu, have the whole HDD without formating my documents?
I'll try to boot the computer with Windows CD, to try to check is there anything on the hard disk.

---

### Post by Locutux on 2008-01-19
You can re-install Ubuntu on the same partition where it's installed now.

---

### Post by Moop on 2008-01-19
> **Commando said:**
> I am using so small part of the disc, because that is the partition that i made when installing the Ubuntu, 10GB. Still, I cant say for sure if my files are deleted or not, because it keeps showing that I have only 6-7 GB free space (thats what has left from the partition space). The partition is ext2 I guess, thats what i chose when I was installing.
I'll ask again: Is there a way to re-install the Ubuntu, have the whole HDD without formating my documents?
I'll try to boot the computer with Windows CD, to try to check is there anything on the hard disk.

No. There is no way to install Ubuntu to the whole hard drive and save any documents or info that's on the hard drive.

---

### Post by smurphy_it on 2008-01-19
You could try copying any important files to a USB flash drive or burning off to a CD.  Then boot with the ubuntu CD and re-install.  I'd make use of the whole hard drive this time, or at least give you space lots more room.

In my specific setup, I have three (3) partitions setup for linux.  1 is a small 10 GB partition for linux, 2nd is a swap partition (1.5-2.5x the amount of RAM you have) and the 3rd is the remainder of my drive setup as a /home partition.  

I like this setup as anytime I re-install ubuntu (or any linux distro) I just do a manual partition setup and tell it not to format my home partition so I don't lose any info.

If you do something the same, I'd have a bigger linux partition than 10 GB.  You have the room, so I'd probably do a 20-30GB, a swap, and the rest for linux (as ext3 or reiserfs).

---

### Post by Yoke &amp; Chung on 2008-01-19
I am sorry to say, it looks like you have formatted your whole hard disk, and your files are gone. Don't do anything to it now, look for some recovery software if you want to recover those files you had on your hd.

---

