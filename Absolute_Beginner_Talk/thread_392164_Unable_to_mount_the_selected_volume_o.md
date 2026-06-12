---
title: "Unable to mount the selected volume :o"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by drab on 2007-03-24
im a nub to linux but anywho ive been trying to make some space to share files between windows xp and ubuntu dapper. i was told that i could easily share between them making a partition into fat32 but i just get errors when i double click on it....is there anyone able to tell me whats to do? :(
o and here is the details in the error 

> error: device /dev/hdc2 is not removable

error: could not execute pmount

---

### Post by PartisanEntity on 2007-03-24
Please post the output of:

```
sudo fdisk -l
```

---

### Post by drab on 2007-03-24
Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       23733   190635291    7  HPFS/NTFS
/dev/hdc2           23734       36483   102414375    c  W95 FAT32 (LBA)

Disk /dev/hdd: 30.0 GB, 30000000000 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3495    28073556   83  Linux
/dev/hdd2            3496        3647     1220940    f  W95 Ext'd (LBA)
/dev/hdd5            3496        3647     1220908+  82  Linux swap / Solaris

---

### Post by bodhi.zazen on 2007-03-24
You can mount the partition with :

```
sudo mkdir /media/hdc2
sudo mount /dev/hdc2 /media/hdc2 -o uid=1000,gid=100,umask=007
```

If you want to use pmount for internal drives you will need to alter a config file. If you want the partition to mount at boot you will need to add an entry to /etc/fstab

See here for details : [http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

for pmount : [http://doc.gwos.org/index.php/Understanding_fstab#Configure_pmount_for_internal_HD](http://doc.gwos.org/index.php/Understanding_fstab#Configure_pmount_for_internal_HD)

Off Topic : Hi PartisanEntity ;)

---

### Post by drab on 2007-03-24
awsome but now im able to freggin share over ntfs... making a second patition on my first hardrive was a damn waste lol >.< thanks a lot for the help. btw when i did the first one with the script it didnt mount the hds right away i had to restart my comp :/

---

