---
title: "can't see ntfs drive in file browser"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by goodmore on 2006-06-22
Tried to mount it using a guide. sudo fdisk -l looks like this
Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4791    38483676   83  Linux
/dev/hdc2            4792        4998     1662727+   5  Extended
/dev/hdc5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       19457   156288321    7  HPFS/NTFS



sudo nano /etc/fstab looks like this.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1 /windows ntfs nls=utf8,umask=0222 0 0











                                [ Read 8 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

Why can't I see my harddrive with file browser?

---

### Post by Apple 101 on 2006-06-22
Does the /windows folder exist on your system? Use mkdir to create it or just use Nautilus.

---

### Post by x64Jimbo on 2006-06-22
Don't know. Why don't you tell us what you've done so far in your efforts and any errors you've encountered along the way?

---

### Post by aysiu on 2006-06-22
Try ```
sudo mkdir /windows
sudo umount /dev/hdd1
sudo mount -a
cd /windows
ls
``` and post the output back here.

---

### Post by goodmore on 2006-06-22
cannot create directory `/windows': File exists


sudo mount -a
cd /windows
ls      I get to see all the files on the harddrive listed in the terminal.

I just do't get to see the harddrive listed in the file browser or Nautilis


I tried to use this guide [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

My Ntfs harddrive was not listed when  I sudo nano /etc/fstab so I used the edit command and put it in there like /dev/hdd1 /windows ntfs nls=utf8,umask=0222 0 0



Thank you

---

### Post by aysiu on 2006-06-22
So when you go to Nautilus and press Control-L and type ```
/windows
``` and hit Enter, what do you see?

---

### Post by goodmore on 2006-06-22
Heey I see all my files. Is there a way to see the harddrive listed in computer with out typing /windows?



Thanx a bunch

---

