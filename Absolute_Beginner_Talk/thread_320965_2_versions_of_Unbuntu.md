---
title: "2 versions of Unbuntu"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Guitar John on 2006-12-18
I installed Ubuntu on my computer, and then I found a different version called [Ubuntu CE]("http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html").  So I thought I would give it a try.

Anyway, I now have 3 OS's on my computer, XP and 2 versions of Ubuntu which I did for a side-by-side comparison.  So my question is, how do I now get rid of the version of Ubuntu that I don't want to keep?

FWIW, in the partition utility (gparted, i think) it is showing 3 partitions.  One is about 93 gB, and the other 2 are 25.26 and 25.27.  How do I find out which OS is on which partition?

---

### Post by Sef on 2006-12-18
The Windows is on the NTFS partition.   Not sure how to tell the two Ubuntu partitions apart.  

Note: From the terminal (Applications > Accessories > Terminal) 

type in sudo fdisk -l and it will tell you your partitions too.

---

### Post by darrenm on 2006-12-18
Boot into one of the Ubuntu you want to keep and run:

```
sudo fdisk -l
```
and
```
mount
```
and let us know the output of both of those

---

### Post by Guitar John on 2006-12-18
> **darrenm said:**
> Boot into one of the Ubuntu you want to keep and run:

```
sudo fdisk -l
```
and
```
mount
```
and let us know the output of both of those


I'm getting "Unable to open"

---

### Post by taurus on 2006-12-18
> **Guitar John said:**
> I'm getting "Unable to open"

Which command would that be, "sudo fdisk -l" or "mount"?

---

### Post by Guitar John on 2006-12-18
1st of all, thanks so much for the quick replies.

Now, when I type > sudo fdisk -| i get > >.
When I type > sudo fdisk  without the > -| I get 


> Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda (for the first IDE disk)
or: fdisk /dev/sdc (for the third SCSI disk)
or: fdisk /dev/eda (for the first PS/2 ESDI drive)
or: fdisk /dev/rd/c0d0 or:fdisk /dev/ida/c0d0 (for RAID devices)

---

### Post by taurus on 2006-12-18
Did you boot into the Ubuntu CE version (the one that you want to keep)?

---

### Post by girishv on 2006-12-18
If you had installed grub again when you installed ubuntu CE, just go to 
/boot/grub  and check out which where CE is installed. It will be next to the kernel image file
like
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/sda2

Yours might be /dev/hda2 or some thing. Similarly you can find out where the other UBUNTU is installed

Girish

---

### Post by Guitar John on 2006-12-18
Ok, I tries a lower case letter " L" after the sudo command.  I was using the symbol above the backslash.  They look the same on my computer.

So now I typed > sudo fdisk -l and I get

> Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot      Start            End            Blocks          ID     System
/dev/sda1    *           1                6            48163+        de    Dell Utility    
/dev/sda2                 7         12268        98494515          7     HPFS/NTFS                  
/dev/sda3           12269        15825        28571602+      83     Linux
/dev/sda4           15826        19452        29133877+       5      Extended
/dev/sda5           19268        19452        1485981          82      Linux Swap / Solaris
/dev/sda6    *     15826        19123        26491122        83      Linux
/dev/sda7           19124        19267        1156648+        82      Linux Swap / Solaris

---

### Post by Guitar John on 2006-12-18
Hopefully this is the shortcut I'm looking for.

I rebooted the computer.  The version of Ububtu that I want to keep is currently the default OS.  

> Other operating systems:
Microsoft Windows XP Home Edition
Ubuntu, kernel 2.6.17-10-generic (on /dev/sda3)
Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda3)
Ubuntu, memtest86+ (on /dev/sda3)

---

