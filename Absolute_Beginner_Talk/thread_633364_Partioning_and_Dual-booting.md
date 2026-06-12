---
title: "Partioning and Dual-booting"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Rezistik on 2007-12-06
I decided I want to give ubuntu a try and torrented it,burned it and popped it in. I opened GParted ti partition my C Drive but it refused to read it, said it was physically damaged (Windows reads it fine..) So I figured I would use my secondary drive, so I cleaned my secondary drive on windows and then I popped ubuntu back in and Gparted read the drive and then I did the partitioning and when I pressed apply, I got an error. So I have two questions one Can I dual boot using two separate drives, Two is it okay that all my drives are NTFS, and I lied  i have a few more questions....What software should I use since Gparted either does not work on NTFS or I fail at using it.

Oh and I cant wipe my secondary drive entirely I freed 17 gigs and am aiming to only use 10 gigs for ubuntu, its my media drive all my music, picturess and .psds so I was also hoping ubuntu could read it.

Thanks in advance :)

---

### Post by ajgreeny on 2007-12-06
Not sure about the physically damaged problem but you need to check that your hard disks are not mounted before you try to do anything with gparted.  So open a terminal and type ```
mount
```If the output contains something like ```
/dev/hda1 on /media/WindowsXP type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
```then the windows disk is mounted.  It will probably show on the desktop as well so right click on the icon if it's there and chose unmount volume which should then mean you can work on the partition/disk with gparted.

You can certainly dual boot with two (or three or more) disks without a problem and ubuntu will work out where everything is and install grub accordingly when you install the OS.  You will not install ubuntu on a ntfs partition, but let the installer format the part of the disk you chose to use for installing, and don't worry about it too much.  The format type will be ext3 by default, so go with that and all should be well.

Let us know how you get on, and if you need more help come back again with questions.

---

### Post by esmerine on 2007-12-06
Didn't want to start a new topic, and my question is about formatting hard disc also.
I am going to install ubuntu on the same hd as windows is (windows uses ntfs), so as I understand, ubuntu (when installed and used) won't be able to write files into my ntfs partition, but I will be able to read and copy files that are there? And what about vice versa - the same? :redface:

---

### Post by betes on 2007-12-06
Ubuntu will be able to read and write files on your NTFS partition, but Windows will not be able to read or write on your Ubuntu partition (etx3, ext2, or whatever).  Also you will be able to copy files over from your windows partition into your ubuntu partition.

Edit: provided you are installing Ubuntu 7.10

---

### Post by rsambuca on 2007-12-06
> **betes said:**
> Ubuntu will be able to read and write files on your NTFS partition, but Windows will not be able to read or write on your Ubuntu partition (etx3, ext2, or whatever).  Also you will be able to copy files over from your windows partition into your ubuntu partition.

Edit: provided you are installing Ubuntu 7.10

Windows can also read and write to the ext3 filesystem if you install the[ fs-drivers for Windows]("http://www.fs-driver.org/").

---

### Post by betes on 2007-12-06
> **rsambuca said:**
> Windows can also read and write to the ext3 filesystem if you install the[ fs-drivers for Windows]("http://www.fs-driver.org/").

Ah! I guess I never realized that because I never use windows, so I've never taken the time to look into it.  Thanks.

---

### Post by StephUb on 2007-12-06
First, start on windows and do a checkdick on startup.
I did a dualboot on my laptop (sony vaio FS) and everything worked the fist time
Also i prefer to use directly the Gparted live CD because ubuntu cd will mount your windows partition

So First check the inetgrity on disk from windows
2. defragment your disk. (hopefully you're not using the windows one, prefer a diskeeper)
3. shrink windows on Gparted
4. reboot on windows to make sure everythings ok (he should run a checkdisk at startup)
5. reboot Gparted live CD
6. Create your partitions
i kept 20G windows 40g NTFS common files 10g home and 15g Ext3 and finally 1.5G swap
7. Install ubuntu and choose advanced/manual and choose the right partitions.
8. For the Grub you have two choice, using the grub form linux at startup or letting windows the boot and use (in) windows a thirdparty grub to access ubuntu (you are actually not booting on windows, you just let the windows booter access ubuntu)
I personnaly used the grub as boot (i did a copy on my mbr before starting the install)

Hope that help

---

