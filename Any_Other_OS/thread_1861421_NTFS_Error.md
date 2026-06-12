---
title: "NTFS Error"
date: 2011-10-15
forum: Any Other OS
---

### Post by Hosmion on 2011-10-15
Hello!  I recently purchased a game on Steam that requires .NET Framework to run.  I tried installing it over Ubuntu but, long story short, errors kept it out.  I just decided I'm going to reinstall my Windows, via my Windows disk I have.  I entered the disk, booted from it so it'll install, and went through some of the settings.

Unfortunately, when it asked what disk to install it on, it said that the disk has to be set to "NTFS" format or something, and it can't install on either of my drives.  

How do I set my drive in that format so I can install Windows?

Thanks,
Leonard

---

### Post by oldfred on 2011-10-15
Moved thread to other OS.

You have to have a primary partition sda1 thru sda4 formated NTFS with the boot flag. Or unallocated space and an available primary partition to use. You can from Windows create partitions and set partition to active (which is boot flag). Or use gparted as windows often damages partition table when Linux partitions exist as it does not see them correctly.

Is disk a full install or just an upgrade or recovery disk. You normally need a full install disk. Recovery may only work to empty drive or one with NTFS partition of same size as original system.

---

### Post by Hosmion on 2011-10-15
The disk is a full install disk.  When I choose which parition to install Windows on it gives me the NTFS error that I don't know how to fix.  

I didn't understand any of the first part of your post.  What should I do so I can install Windows?  If you can answer it simply, that'd be great, because apparently I cannot understand all this complicated stuff.

---

### Post by oldfred on 2011-10-15
From Ubuntu or Ubuntu liveCD terminal post this.

sudo fdisk -lu

Or a screen shot from gparted.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

This is old as now you have to reinstall grub2's boot loader.
Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 with grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

### Post by Hosmion on 2011-10-15
sudo fdisk-lu:


```
lenni@lenni-Aspire-6930:~$ sudo fdisk -lu
[sudo] password for lenni: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e2d91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480284671   240141312   83  Linux
/dev/sda2       480286718   488396799     4055041    5  Extended
/dev/sda5       480286720   488396799     4055040   82  Linux swap / Solaris
lenni@lenni-Aspire-6930:~$ 
```

I'm working on the rest of your tutorial, so I will edit this as I go along, so if you have more information to add, go ahead.

---

### Post by oldfred on 2011-10-15
Your sda1 is large and you can shrink it with gparted. Then in gparted move boot flag to new NTFS partition that you create in the free space. It will become sda3 which is a primary partition.

I might also create a shared NTFS partition also. You should not write into the Windows system partition from Ubuntu but can read from it. With a shared partition you can read & write from both systems for any data you might want to share. I shared Firefox & Thunderbird profiles so my email & bookmarks were the same.

---

### Post by Hosmion on 2011-10-15
You should make a video on how do do this cause it's kind of confusing.  Im in GParted and everything, but how much do I shrink the partition?  And what is a "boot flag"?

---

### Post by oldfred on 2011-10-15
If you click on sda1 and then right click it will have manage flags. Turn boot off. Then in the new partition do the same but add boot flag.

I thought the link on gparted had screen shots. I believe this does also.
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

There may be videos. I just do not have any links. I find it hard to follow a video as I want to do something at the same time. Screen shots let me do it, then move to the next screen.

---

### Post by Gs Dewd on 2011-10-16
Is windows the only thing your going to install on this drive? If so use the win cd to format the drive to ntfs. Or go to the drive manfacturers web site and download whatever tools thay have and format the drive with that. When yuor done the drive will have 1 ntfs partition on it thats all.

---

