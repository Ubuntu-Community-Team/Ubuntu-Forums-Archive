---
title: "[SOLVED] which partition to delete?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by camellochapin on 2008-02-14
I had a problem installing linux (Xubuntu 7.10) on my PC.  On my first try, the PC ran out of battery in the middle of the installation process... afterwards I reinstalled it again... but of course, it created a new partition same size as the first one, and also the swap partition... same size as the first one.

So... all this brings me to the main problem.  I have to reinstall "Windus" on this machine... not because I want, but because I have to... it's the company's PC and tons of software we use runs just in "Windus" :-x :-x

While trying to reinstall windus, it says that the hard drive ran out of partitions, it already has 4 (twice swap and twice linux, same size)...  Of course there is one swap and one linux which doesn't work, so I want to delete them...

... how to know which one is which?  

Thanks for your help!

---

### Post by stevejesus on 2008-02-14
Delete ALL your Linux partitions, and THEN start over.

---

### Post by camellochapin on 2008-02-14
> **stevejesus said:**
> Delete ALL your Linux partitions, and THEN start over.

Ehemmm... delete??  sorry but I already have stored files and configurations... I know, I can back them up, but wouldn't it be easier just deleting the proper ones?

---

### Post by Inxsible on 2008-02-14
post the output of ```
sudo fdisk -l
``` and also your fstab```
cat /etc/fstab
```

---

### Post by camellochapin on 2008-02-14
> **Inxsible said:**
> post the output of ```
sudo fdisk -l
``` and also your fstab```
cat /etc/fstab
```

```
jpablo@jpablo-laptop:~$ sudo fdisk -l
[sudo] password for jpablo:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09b5ea03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        7391       10764    27101652   83  Linux
/dev/sda2           10765       14142    27131904   83  Linux
/dev/sda3           14143       14293     1212868   82  Linux swap / Solaris
/dev/sda4           14294       14594     2417782+   f  W95 Ext'd (LBA)
/dev/sda5           14294       14593     2409708   82  Linux swap / Solaris

```

and 

```
jpablo@jpablo-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=cb80d777-4fff-4490-99f2-79ec5c14ce5a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=18dd7ec6-0152-4479-81a1-ec459169dbfe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by Thingymebob on 2008-02-14
those comments in fstab can't be right /dev/sda6 & /dev/sda7 don't appear in fdisk-l
Can you post the output of ```
blkid
```

---

### Post by camellochapin on 2008-02-14
> **Thingymebob said:**
> those comments in fstab can't be right /dev/sda6 & /dev/sda7 don't appear in fdisk-l
Can you post the output of ```
blkid
```

```
jpablo@jpablo-laptop:~$ blkid
/dev/sda1: UUID="39586dc1-e242-4dfd-b994-74be468659e1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="cb80d777-4fff-4490-99f2-79ec5c14ce5a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="18dd7ec6-0152-4479-81a1-ec459169dbfe" 
/dev/sda5: TYPE="swap" UUID="3f8cd229-c3be-476c-ac95-dce63a35a15e" 

```

By the way... thanks a lot for your help guys!  I really appreciate it!

---

### Post by Thingymebob on 2008-02-14
Looks like your installation is using /dev/sda2 as the root partition and /dev/sda3 as the swap
(swap) /dev/sda5 can be removed and
(root /)/dev/sda1 can be removed

---

### Post by camellochapin on 2008-02-14
> **Thingymebob said:**
> Looks like your installation is using /dev/sda2 as the root partition and /dev/sda3 as the swap
(swap) /dev/sda5 can be removed and
(root /)/dev/sda1 can be removed

Thanks a lot for your help!  At least now I know which partitions to delete... is there any command to do it?

---

### Post by Thingymebob on 2008-02-14
add remove programs and search gparted and install
hit alt & F1 type gksudo gparted

---

