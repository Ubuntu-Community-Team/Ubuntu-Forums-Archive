---
title: "need help accessing sdb1"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by RJ Hythloday on 2008-03-01
My system crashed, I was using an edubuntu on hdd 2 and it crashed, I'm back on hdd1 w/ kubuntu and need to get 1 file off of the edubuntu hdd. 

I'll install something on hdd2 if needed to access something out of the home partition. I hope it made on by default, this is all still very new to me.

To be completely honest I'm afraid to hook up my .flac hdds. I need to move data from a 200 and 400 to a 750 so they can be reformatted ext3 but I'm scared!

Right now can someone just help me get the one file off of sdb1?

I get this message
> hal-storage-fixed-mount refused uid 1000

---

### Post by glennric on 2008-03-01
Can you post the output of 
```
sudo fdisk -l
```
and 
```
cat /etc/fstab
```

---

### Post by RJ Hythloday on 2008-03-01
```
sudo fdisk -l
```
Disk /dev/sda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa935a935

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2386    19165513+  83  Linux
/dev/sda2            2387        2495      875542+   5  Extended
/dev/sda5            2387        2495      875511   82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ea14af3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2372    19053058+  83  Linux
/dev/sdb2            2373        2480      867510    5  Extended
/dev/sdb5            2373        2480      867478+  82  Linux swap / Solaris


```

cat /etc/fstab
```# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=59ca9f25-e838-42ca-9246-5806c87e65e6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=97e32056-da26-43dc-8657-9f5ba7154e79 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by RJ Hythloday on 2008-03-02
^^ any one? not sure how my partitions were automatically set up, will I be able to get any thing?

---

