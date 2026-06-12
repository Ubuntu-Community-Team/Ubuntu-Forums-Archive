---
title: "Weirdest PROBLEM EVER!!!!!"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-01-17
I recently re downloaded XP to try somthing out, but I think I removed my linux swap in the process. Now when I'm in ubuntu and I go to gparted it says no parts of my HD are used so I cant delete XP. AND i cant download another OS..(probly gOS) any one know what I can do?

---

### Post by nikoPSK on 2008-01-17
Putting windows over linux in a dual boot usually ends up bad...

---

### Post by nikoPSK on 2008-01-17
> **nikoPSK said:**
> Putting windows over linux in a dual boot usually ends up bad...

By that I mean, it will do things to grub... best to install linux over windows. :)

---

### Post by dstew on 2008-01-17
You need to run gparted from a disk other than the one you want to work on. You can download a gparted LiveCD to do this, or boot an Ubuntu LiveCD and use gparted from there. You might need to install if using Synaptic on the LiveCD system before you can use it. The [gparted LiveCD]("http://gparted-livecd.tuxfamily.org/") is best.

---

### Post by nikoPSK on 2008-01-17
test disk should help ya too. :)

---

### Post by -gabe-noob- on 2008-01-17
I think I might not be getting through right. I can boot into ubuntu, but when I used G parted in ubuntu it say there is nothing on my HD. I think its cause I deleted my linux swap or somthing. also when I boot from livei t also says there is NOTHIN on my harddrive, although there is!


Thank you for your replys

---

### Post by erginemr on 2008-01-17
Your title does justice to your problem: This is really one of the weirdest problems.

I have nothing up my sleeve but wild guesses. Seems to be a UUID incompatibility issue to me, or maybe Linux swap as you pointed out... Could you please post the outputs of the following three commands:
```
cat /etc/fstab
sudo fdisk -l
blkid
```

---

### Post by morgan_greywolf on 2008-01-17
It sounds to me like you have a partially corrputed partition table.  Things could get ugly. You may have to back everything up on your Windows and Linux partitions and re-install everything.

---

### Post by dstew on 2008-01-17
> when I boot from livei t also says there is NOTHIN on my harddriveWhat do you mean by this? Do you mean you cannot see your hard drive using the LiveCD file management programs, or that you cannot see your hard drive in a disk partitioner program, like gparted?

---

### Post by -gabe-noob- on 2008-01-17
Ok well I'm on a school computer now... but I'll check this out on my laptop. Also  what happens is on the live, and g parted is that it says that the whole 80 gig volume is un alocated


I'll type ut the results of the tests now. 

damn times up on comp I'll post them around 5'00 clock eastern time

---

### Post by dstew on 2008-01-17
> g parted is that it says that the whole 80 gig volume is un alocatedIs this gparted running from the LiveCd or from your hard disk Ubuntu installation?

---

### Post by Pogeymanz on 2008-01-17
Your partition table just got screwed up. It happens.

Google for TestDisk, download it, burn it, read some instructions and use it. It should find your partitions and restore your table with no problem.

---

### Post by nikoPSK on 2008-01-17
> **EmosSuck777 said:**
> Your partition table just got screwed up. It happens.

Google for TestDisk, download it, burn it, read some instructions and use it. It should find your partitions and restore your table with no problem.

it's quite a useful app. +1

---

### Post by -gabe-noob- on 2008-01-17
Both Ubuntu in live and my Ubuntu show an un allocated in g parted, and I'll go check out test disk, thanks for the repys.

---

### Post by -gabe-noob- on 2008-01-17
How do you download a tar.zg ?

---

### Post by -gabe-noob- on 2008-01-17
For the person who wanted me to put in codes 


here they are:gabe@gabe-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=2c4d9a59-254b-41b2-add0-2d291d375450 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=31e0075e-8aba-4707-afce-07f1403c76f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
gabe@gabe-laptop:~$ sudo fdisk -l
[sudo] password for gabe:
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1985    15944481    7  HPFS/NTFS
/dev/sda2            1986        9436    59850157+  83  Linux
/dev/sda3            9445        9729     2289262+   5  Extended
/dev/sda4            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sda5            9446        9541      771088+  82  Linux swap / Solaris
gabe@gabe-laptop:~$ blkid
/dev/sda1: UUID="A0CCEB9FCCEB6E4A" TYPE="ntfs" 
/dev/sda2: UUID="2c4d9a59-254b-41b2-add0-2d291d375450" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="0302b1b3-c7b6-4358-acff-c3d7d3b91c77" 
/dev/sda4: UUID="31e0075e-8aba-4707-afce-07f1403c76f9" TYPE="swap" 
gabe@gabe-laptop:~$

---

### Post by erginemr on 2008-01-18
Apparently, your swap file is in effect. Please read the following ongoing thread, in which the OP is bothered with a problem similar to yours:
[http://ubuntuforums.org/showthread.php?t=670094](http://ubuntuforums.org/showthread.php?t=670094)

You may consider adding the appropriate line to /etc/fstab as I tried to explain in that thread. You can download and run testdisk with:
```
sudo aptitude install testdisk
```
It is in the repositories. Or if you still have access to Windows, you can also download and run testdisk from within windows.

---

