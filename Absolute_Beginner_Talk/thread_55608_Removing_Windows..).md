---
title: "Removing Windows..:)"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by cnayak on 2005-08-09
I guess I'm pretty comfortable with Linux. So, it's high tome to ditch Windows. I have a 40 gb hdd and it is partitioned in the following manner:

  1. 8gb - NTFS , Win XP

  2. 1 gb - swap

  3. 4gb - ext2

  4. Rest in FAT32 format. This is very important as all of my files are stored here.

 
 Now I want to delete the NTFS partition and append the free space to the ext2 partition. I also need to configure GRUB to boot into Ubuntu directly. How do I proceed?

  PS: Is it possibe to format the FAT32 partition to ext2 and still retain all the data?

---

### Post by varunus on 2005-08-09
You might want to just shrink the windows partition to as small as possible instead.  Just in case, y'know...bad things can happen, even to linux.

You can change which os boots by default by editing /boot/grub/menu.lst.  There's a "default" line in there, change the number to change the default.

I don't think there's an easy way to just append the NTFS onto the ext2 partition (why are you using ext2 instead of ext3, btw?).  I don't know if gparted can move partitions around without destroying them, and the NTFS one is first...

Here's a howto on how to install partitioning software:
[http://www.ubuntuguide.org/#gparted](http://www.ubuntuguide.org/#gparted)

---

### Post by aysiu on 2005-08-09
You know, any resizing or reformatting of existing partitions could screw the integrity of your data, anyway. If you ask me, the best thing to do is back up your documents and settings (CD, external hard drive, MP3 player, whatever--borrow a friend's if you don't have one), then reinstall Ubuntu and have it erase the entire drive. Then, copy back your documents and copy back your settings. It sounds excessive, but if you know for certain you don't want Windows any more, this is the cleanest way to do it, and it will serve you the best down the line.

---

### Post by SunshineSmile on 2005-11-03
I would like to try tampering with the partitions, even though it might screw up some data. If something goes wrong I can always boot up the CD with Ubuntu, right?

I fetched **gparted** using **synaptic package manager** (found under System-->Administration-->Synaptic Package Manager. Hit the search button, typed in gparted, marked for installation, hit apply, and now I have gparted.

Well: [SIZE="3"]***I want to add more GB to my Ubuntu partition, and shrink or delete wholly my Windows ME partition.* **[/SIZE]Windows Me didn't work properly anyway, couldn't find all the drivers for my screen or audio..

Now I have gparted up and running. Could anybody explain how this works?

It says: 
Partition     -  Filesystem      -  size(MB)      --   used(MB    -  unused(MB)    -- flags
/dev/hda1        fat32            28,608                  1,731             26,877          boot lba
/dev/hda2        ext                 9,131                   9,120                   11
/dev/hda3        extended          424                   -----
     /dev/hda5   Linux-swap        424                   ----


Okay, if anybody could help me, I wanna get rid of/or shrink that /dev/hda1 and free all the space for my (ongoing) megatorrents. Pretty please?:p

---

