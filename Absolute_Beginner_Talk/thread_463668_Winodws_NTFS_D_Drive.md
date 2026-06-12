---
title: "Winodws NTFS D Drive"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Paulie Walnuts on 2007-06-03
If I install Ubuntu on my C Drive (where I keep my operating system and program files) will it recognize the data I store on my D drive that is formatted with NTFS?

---

### Post by Bohlio on 2007-06-03
Are you getting rid of windows completely? or are you just going to install both operating systems on the same drive? Well anyways, If you are going to dual boot with both Operating Systems, When you are in Ubuntu, you will be able to read files from your windows partition (C drive) and your other hard drive (D drive) although in ubuntu they are not refered to as your C or D drives. You will need to install special drivers like NTFS-3G in order to write to the drive, but you will be able to read from the drive right outta the fresh install unless you have some weird unsupported hardware problem. :-)
I hope i helped :-P

---

### Post by Inxsible on 2007-06-03
> **Paulie Walnuts said:**
> If I install Ubuntu on my C Drive (where I keep my operating system and program files) will it recognize the data I store on my D drive that is formatted with NTFS?

First of all, there are no drive letters in Linux. So the OS is always on the root - denoted by / - partition. And yes, you can access any files on your NTFS partitions as read only.

If you want write access, you will need to install ntfs-3g / ntfs-config.

---

### Post by Inxsible on 2007-06-03
Got beat by Bohlio :)

---

### Post by Bohlio on 2007-06-03
Lol, Still its always good to get the same information from many members than to have just one persons input :-P

---

### Post by jaybuntu on 2007-06-03
Yes, Ubuntu can read and write NTFS as well as FAT partitions.  Drive letters are a left over convention from way back in the olden days of DOS, so your "D" drive might appear as "\media\hda2" or something similar.  If you plan to dual boot for a while, you probably don't want to install directly to you "C" drive.  I would recommend shrinking your "C" partition and then installing Ubuntu into the new free space unless your ready to go cold turkey and give up Windows.

---

### Post by Bohlio on 2007-06-03
On a relavent side topic, How is the name of the drive decided (hda2, sda1, ect ect...)  and what is an easy way to check which drive/partition is named what? Thanks.

And jaybuntu, Can Ubuntu read and write NTFS natively? If so, I missed that one as I installed NTFS-G3.

---

### Post by Inxsible on 2007-06-03
It can read NTFS...but cannot write to it without ntfs-3g

---

### Post by Inxsible on 2007-06-03
h = ide drives
s = sata drives

hda is the first disk
   hda1 is the 1st partition on the 1st disk
   hda2 is the 2nd partition on the 1st disk

hdb is the second disk
   hdb1 is the 1st partition on the 2nd disk
......

and so on...

Simply replace h by s for sata drives

---

### Post by Bohlio on 2007-06-03
Thank you very much, I've been learning about 5 new things about Ubuntu a day from these forums :-P

---

### Post by =JeffH on 2007-06-08
Some of the info in this post may be helpful...

[http://ubuntuforums.org/showpost.php?p=2806660&postcount=4](http://ubuntuforums.org/showpost.php?p=2806660&postcount=4)

=JeffH

---

### Post by ccfjeff on 2007-06-08
> **Inxsible said:**
> h = ide drives
s = sata drives

hda is the first disk
   hda1 is the 1st partition on the 1st disk
   hda2 is the 2nd partition on the 1st disk

hdb is the second disk
   hdb1 is the 1st partition on the 2nd disk
......

and so on...

Simply replace h by s for sata drives

Sorry to jump into someone else's discussion, but wouldn't that mean that Linux is just changing the names from "drive" to "disk"?

---

### Post by Inxsible on 2007-06-08
> **ccfjeff said:**
> Sorry to jump into someone else's discussion, but wouldn't that mean that Linux is just changing the names from "drive" to "disk"?
 
Drives -- Disk.........Tomatoes - Toma(h)toes :rolleyes: (more or less ;) -- Couldnt think of another analogy ) 
 
Drive and Disk can be used interchangeably to mean the same thing.

---

### Post by ccfjeff on 2007-06-08
> **Inxsible said:**
> Drives -- Disk.........Tomatoes - Toma(h)toes :rolleyes: (more or less ;) -- Couldnt think of another analogy ) 
 
Drive and Disk can be used interchangeably to mean the same thing.

Ok, thanks.  (Sorry for the interruption).  Now back to the regular programming...

---

### Post by Vajk on 2007-06-08
> **Paulie Walnuts said:**
> If I install Ubuntu on my C Drive (where I keep my operating system and program files) will it recognize the data I store on my D drive that is formatted with NTFS?

If you want to use only Ubuntu then it's ok to install on that partition and yes, you'll be able to read and write to NTFS partition with ntfs-config. But if you will keep your other OS then it's better to install it on a different partition, you will need to format it to ext3 filesystem (the format can be done during ubuntu install)
I hope it helped

---

