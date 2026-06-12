---
title: "[SOLVED] Mount Points - I'm just not getting this..."
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2007-12-14
Coming off a new install of Ubuntu 7.10 and I'm just not grasping mount points. I've been reading through posts and Wiki's and maybe I'm just overthinking this, but I need some help. 

Points of confusion:

After I turn on the computer, when I pull up Computer - File Browser - Ubuntu shows all 3 of my physical hard drives listed as follow:

465.8 GB Volume: disk
Backup
Filesystem

465.8GB Volume: disk is unmounted



The end goal is trying to get the disk labeled "465.8 GB Volume: disk" to automatically mount to /mnt/sdb1each time the PC starts. 

I don't know how to tell the difference between "465.8 GB Volume: disk" and "Backup" as both are same model and size hard drive - the only difference is that "Backup" has all of my important data.

Question 1: Where is Ubuntu pulling the names of each physical drive from? 
Question 2: How can this name be changed?
Question 3: : How does one translate the names shown in Computer - File Browser to the results of "fdisk -l" ?

Here's my current config:

```


 sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39d8444f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76ef76ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabbe68bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488384512    7  HPFS/NTFS



```


And

```

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6e84aa48-670a-49d7-b335-4c5de16a9c05 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=04301ec8-4a53-413f-9da6-e1abd8fa4ebc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```


I'm not sure how to move forward from here.

---

### Post by Duck2006 on 2007-12-14
This may help, for windows

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

and for linux

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by thelatinist on 2007-12-14
One way to find your device's name:

1) Go to System > Preferences > Hardware Information.

2) Find your device in the left pane.  Click on it.  Then click the Advanced tab and look at the string value for the block.device key.

---

### Post by pjkoczan on 2007-12-14
> **vortex0007 said:**
> Coming off a new install of Ubuntu 7.10 and I'm just not grasping mount points. I've been reading through posts and Wiki's and maybe I'm just overthinking this, but I need some help.

Mount points were a bit confusing to me at first, but once I saw how they can be used, and got a little experience with them, I loved them. Hopefully the same holds true for you.

> Points of confusion:

After I turn on the computer, when I pull up Computer - File Browser - Ubuntu shows all 3 of my physical hard drives listed as follow:
...
The end goal is trying to get the disk labeled "465.8 GB Volume: disk" to automatically mount to /mnt/sdb1each time the PC starts. 


Mount points don't survive a reboot unless they have an entry in /etc/fstab. I'll get to that later.

> I don't know how to tell the difference between "465.8 GB Volume: disk" and "Backup" as both are same model and size hard drive - the only difference is that "Backup" has all of my important data.

Question 1: Where is Ubuntu pulling the names of each physical drive from? 
Question 2: How can this name be changed?
Question 3: : How does one translate the names shown in Computer - File Browser to the results of "fdisk -l" ?


1. I'm not sure where Ubuntu is pulling the names from, my guess is that it's from a partition label of some sort (I think fdisk allows you to label a partition and refer to it or mount it from a chosen name rather than a device name, don't quote me on the fdisk part, though), defaulting to "X size volume."

2. fdisk, parted, and other partitioning tools allow you change partition names. ALWAYS BE CAREFUL WHEN ALTERING PARTITIONS, even if it's just the name. you may end up doing something you don't want.

3. fdisk is showing the disk stats by device name. Ubuntu does some translation somewhere and the result is a nicer name. Basically, /dev/sd* refers to a SATA or SCSI drive, with a being the first drive the motherboard reports to the OS (likely the SATA 0 port on the motherboard).

/dev/sda1 is the first partition on the first disk, /dev/sdb3 is the third partition on the second disk, etc.

> 
Here's my current config:

...

I'm not sure how to move forward from here.

As previously mentioned, you need to edit /etc/fstab. Since you said that "The end goal is trying to get the disk labeled "465.8 GB Volume: disk" to automatically mount to /mnt/sdb1each time the PC starts," here's what you need to add.

```

/dev/sdb1          /mnt/sdb1each                ext3    defaults        1 2

```

This will tell linux to mount the filesystem on the first partition of /dev/sdb at the given directory, it will try to mount as an ext3 filesystem (which is likely what you have), with the given options ([http://www.humbug.org.au/talks/fstab/fstab_structure.html](http://www.humbug.org.au/talks/fstab/fstab_structure.html) explains these options well).

You can also use the command "mount" (without any arguments) or "df" to get detailed information on mount points and disk partitions.

Note that the directory /mnt/sdb1each will need to exist prior to mounting. You may need to change some arguments in the fstab entry or the mount command if this doesn't work. Best of luck.

---

### Post by stchman on 2007-12-14
> **vortex0007 said:**
> Coming off a new install of Ubuntu 7.10 and I'm just not grasping mount points. I've been reading through posts and Wiki's and maybe I'm just overthinking this, but I need some help. 

Points of confusion:

After I turn on the computer, when I pull up Computer - File Browser - Ubuntu shows all 3 of my physical hard drives listed as follow:

465.8 GB Volume: disk
Backup
Filesystem

465.8GB Volume: disk is unmounted



The end goal is trying to get the disk labeled "465.8 GB Volume: disk" to automatically mount to /mnt/sdb1each time the PC starts. 

I don't know how to tell the difference between "465.8 GB Volume: disk" and "Backup" as both are same model and size hard drive - the only difference is that "Backup" has all of my important data.

Question 1: Where is Ubuntu pulling the names of each physical drive from? 
Question 2: How can this name be changed?
Question 3: : How does one translate the names shown in Computer - File Browser to the results of "fdisk -l" ?

Here's my current config:

```


 sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39d8444f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76ef76ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabbe68bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488384512    7  HPFS/NTFS



```


And

```

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6e84aa48-670a-49d7-b335-4c5de16a9c05 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=04301ec8-4a53-413f-9da6-e1abd8fa4ebc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```


I'm not sure how to move forward from here.

I have a tutorial on partition access.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by vortex0007 on 2007-12-14
Thank you everyone for the links.

A few more hours of reading and I was finally able to make this work.

---

### Post by thelatinist on 2007-12-14
Glad you got the help you needed.  Don't forget to set the thread to [Solved] using thread tools.

---

