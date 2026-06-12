---
title: "I'm having a hard time formating to ext3. PLEASE HELP"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by hotweiss on 2007-09-27
For the last two days I've been trying to format my new external hard drive to ext3. I used Parted Magic (really awesome) to do it without any problems. My system boots and mounts it automatically the FIRST time. The second time time around GRUB freezes and I cannot boot Ubuntu. If I disconnect it, boot Ubuntu and then connect it Ubuntu does not mount it.  If I try to format it in Ubuntu using Gparted I get all sorts of errors. First of all there is a yellow triangle beside it in Gparted. When I right click on information it tells me that the filesystem is damaged, the filesystem is unknown and there is no available file system. I can delete the partition, but when I try to format it I get an error and it reverts back to the old partition. The weird thing is that its listed at /dev/mmcblk0p1? fdisk -l shows me this:

> Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

Any ideas? I've successfully formated the drive many times with Parted Magic and the Gparted live CD, but when I boot into Ubuntu everything goes wrong after the second reboot. It was working fine with FAT32.

---

### Post by Pumalite on 2007-09-27
DBan the drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/) and then reformat ext3 using Gparted:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (the stand alone, burn to CD, boot from, program)

---

### Post by hotweiss on 2007-09-27
How do I use Dban? After it loaded it showed 4 partitions? Which one is which? Only the first one identified itself as Toshiba...

---

### Post by Pumalite on 2007-09-27
You are trying to reformat the whole drive...no? So, DBan the whole drive.

---

### Post by hotweiss on 2007-09-28
Yes, yes, I am trying to format the drive, but I don't know which drive to select in Dban. When I boot up I get these options in Dban:

Toshiba (0,1,1)
hard drive (0,1,1)
hard drive (0,1,1)
hard drive (0,1,1)

Which of the hard drives is my external one? These results are shown with only the master and external drive connected to the computer.

I'm thinking of formating it back to FAT32 in Parted Magic and then formating it to ext3 in Ubuntu.

---

### Post by hotweiss on 2007-09-28
Even if I partition the drive with Gparted into FAT32 it still doesn't work in Ubuntu. Now I'll try with Windows.

---

### Post by hotweiss on 2007-09-28
I noticed that my SD card reader also has disappeared, but thanks to this occurrence I now know what has happened. My hard drive took my SD card's mount point! Hence the mmc01blk mount point. Now I have to figure out how to undo all this mess...

---

### Post by Sef on 2007-09-28
> I used Parted Magic (really awesome) to do it without any problems.

PM and GNU/Linux do not get along well.   Use GParted to check your hard drive.  Best to use Test Disk which is on the disk (under utilities, I believe.)

---

### Post by hotweiss on 2007-09-28
I am just going to download Gutsy Gibbon now... I got the same error when I formatted the drive using Gparted.

---

### Post by hotweiss on 2007-09-28
It keeps on mounting my external hard drive at my SD card's mount point:

[[IMG]http://img231.imageshack.us/img231/4815/screenshotkb6.th.png[/IMG]](http://img231.imageshack.us/my.php?image=screenshotkb6.png)

And that's why either one won't work any more. Wish me luck with Gutsy GIbbon.

PS-does anyone know if the Western Digital My Book has any compatibility issues with Ubuntu?

---

### Post by Pumalite on 2007-09-28
[https://answers.launchpad.net/ubuntu/+question/4390](https://answers.launchpad.net/ubuntu/+question/4390)
[http://ubuntuforums.org/showthread.php?t=207636](http://ubuntuforums.org/showthread.php?t=207636)
[http://www.linuxquestions.org/questions/showthread.php?t=496707](http://www.linuxquestions.org/questions/showthread.php?t=496707)

---

### Post by hotweiss on 2007-09-28
Believe it or not, but I've already read all of those threads. OK I exchanged the WD for a Seagate drive, but I still get the exact same symptoms. My SD card works after formating it in Windows, but I did loose all the data on it. Although now, I see the new drive in Gparted but the old one is still showing, yet I don't have it plugged in. I think a reinstall is my only cure.

---

### Post by Pumalite on 2007-09-28
Good luck.

---

### Post by hotweiss on 2007-09-29
Yes, something really bad is going on! After I plugged in my USB thumbdrive to back up some files, all of my external hard drives disappeared. See you after the install, will let you know how it goes.

---

### Post by hotweiss on 2007-10-01
OK, this problem has been solved in my case. I can't have more than 4 drives connected at startup. It seems to be a BIOS bug, as I reproduced the same error after installing Windows XP Pro, the computer freezes right at the beginning. Oh boy, time to intall Ubuntu AGAIN. I'm sorry for even thinking of blaming Ubuntu, lol.

---

### Post by asmoore82 on 2007-10-01
Western Digital "My Book" mini-HOWTO ***

Today, Sunday, Sept. 30, was my birthday and I got a 500 GB Western Digital "My Book"
These are the steps I took to get it Assimilated into my Ubuntu GNU/Linux system:

0. I already had gparted installed
```
sudo apt-get install gparted
```
0.1. my drive became **sdb**, your mileage may vary

1. Connected My Book, mounted its default vfat just to peek at it, unmounted it and
```
sudo dd if=/dev/zero of=/dev/sdb
```
waited a few seconds and Ctrl+C to stop dd; I really just wanted to blank
the partition table(DBan is my definition of bloatware).
2. Open "System -> Administration -> GNOME Partition Editor"
2.a. Switch to /dev/sdb
2.b. "Device -> set disklabel" and "Create"
2.c. Rightclick on empty space and "Format to -> ext3"
2.d. click "Apply" ~ the final step(creating ext3) takes quite a while
3. set volume label of new ext3 filesystem to "My Book"
```
e2label /dev/sdb1 "My Book"
```
4. set reserved blocks to zero
```
tune2fs -r 0 /dev/sdb1
5. created a new rule in gconf so that "on-the-fly" ext3 systems will be mounted with "noatime"
[code]gconftool-2  -t list --list-type=string -s /system/storage/default_options/ext3/mount_options "[noatime]"
```
6. Mounted "My Book" graphically
7. created a user folder for my username on the command line
```
~$ cd /media/My\ Book
My Book$ sudo mkdir asmoore
My Book$ sudo chown asmoore:asmoore asmoore
My Book$ chmod 700 asmoore
```

Done.

---

### Post by hotweiss on 2007-10-01
Thanks for the great tutorial, but I have already exchanged it.

---

### Post by carbine000 on 2007-10-30
edited....

---

