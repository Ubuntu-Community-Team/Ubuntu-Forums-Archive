---
title: "Just installed Ubuntu and can't find 2nd hard drive with all my data"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by cbrody on 2007-01-29
I always keep all of my data on a second hard drive since I have had to install windows too many times to think about and I didn't want to lose my data.  I just installed Ubuntu on a swappable primary hard drive which shows up fine in my computer but my secondary hard drive only shows up in device manager and not when I click on the my computer icon.  I don't know how to access this drive.  Please help.  I am brand new to linux and willing to learn.

Thanks.
CB

---

### Post by BarfBag on 2007-01-29
Sounds like it isn't mounted.  What file system is it formatted in, and what drive number is it (hda1, hda2, etc.)?

---

### Post by mikewhatever on 2007-01-29
Can you please clarify which of the drives are you not able to access. Suppose, hd1 has ubuntu, and hd2 has windows. Is that correct?

---

### Post by cbrody on 2007-01-29
I can swap out my primary hard drive so that I have a windows installation on another primary hard drive.  Right now, I have ubuntu on my master hard drive dev/hda and I have all of my data on a partitioned drive on my IDE slave drive dev/hdb.  I can't find the slave drive.

CB

---

### Post by taurus on 2007-01-29
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by shoaibi on 2007-01-29
open terminal
use sudo fdisk -l
check if you hard disk entries appear there.
tell me what is it? FAT? NTFS?
and i will tell you the commands to mount that drive....

[Edit]:
go to taurus's link, there will find a lot of stuff which will help you.

---

### Post by cbrody on 2007-01-29
Okay, thanks for replying.  I followed the link from Taurus and followed the instructions.  My data partition was found at /dev/hdb3  hpfs/ntfs and I added it to the fstab file and saved it.  I then looked in the computer icon and I still don't see the partition.  I rebooted as to the instructions and I still don't see it.  Where should I be looking?  What else do I have to do?

Thanks.

CB

---

### Post by shoaibi on 2007-01-29
go to FileSystem
then go to the folder you mounted, you should find it there
and if its not there then probably you didn't mounted it properly,
Lets hope you find it there.

[EDIT]
btw instead of restarting you cna try mount -a in terminal, i am not sure wether the icon will appear or not but fstab will be loaded again.

---

### Post by cbrody on 2007-01-29
Thanks.  I found it. Case closed.

CB

---

### Post by gglbr on 2007-11-19
I have the similar problem of not seeing 2nd drive and I could not mount it.

this is the info from fdisk -l:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x851f851f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e3a82f7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/hdb2            2433       16709   114680002+   f  W95 Ext'd (LBA)
/dev/hdb5            2433        4864    19535008+   b  W95 FAT32
/dev/hdb6            4865       16709    95144931    b  W95 FAT32

I tried Taurus's link, but is it for mounted drives? mine is not mounted at all and 

":~$ sudo mount /media/hdb1
mount: can't find /media/hdb1 in /etc/fstab or /etc/mtab"

Anyone can help me on this one? Thanks!!

---

### Post by shoaibi on 2007-11-19
i would recommend you to read the page that taurus told again, it does have a heading Examine the partition table.... start reading from Examine the partition table.

---

### Post by Zack McCool on 2007-11-19
> **gglbr said:**
> 
":~$ sudo mount /media/hdb1
mount: can't find /media/hdb1 in /etc/fstab or /etc/mtab"

Anyone can help me on this one? Thanks!!

You need a mountpoint.  You also need some options...

```

sudo mkdir /mnt/windows
sudo mount -t vfat -o rw,user /dev/hdb1 /mnt/windows

```

You could also put the entry into your /etc/fstab file to have it automounted at boot.

---

