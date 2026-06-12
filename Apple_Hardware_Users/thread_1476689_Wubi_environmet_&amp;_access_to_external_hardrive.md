---
title: "Wubi environmet &amp; access to external hardrive"
date: 2010-05-08
forum: Apple Hardware Users
---

### Post by mackaframa85 on 2010-05-08
I've created a wubi environment on my mac in the windows partition and have only found one issue, storage.  Wubi limits the installation size to 30GB so I was wondering how I would gain access to write data on my external hard drive.   I have a Seagate free agent external drive and when I try to save data to it it says " error destination is read only ".  And I'm pretty new to linux in general so basic simplified instructions would help me a ton.


Thanks, Any help is greatly appreciated

---

### Post by P4man on 2010-05-08
What filesystem is on that drive? If you formatted it under OS-X I assume its hfs(+), and it may just be a question of setting permissions. But lets see first, open a terminal (applications > accessoires > terminal) and type

```
sudo fdisk -l
```

note, that is -L in lowercase. copy paste the output here, it will show all drives and partitions and filesystems

---

### Post by mackaframa85 on 2010-05-08
I typed in the terminal command and it resulted in this output.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002eac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       23116   185466880   af  HFS / HFS+
/dev/sda3   *       23132       30402    58394624    7  HPFS/NTFS

Disk /dev/sdb: 2021 MB, 2021654528 bytes
63 heads, 62 sectors/track, 1010 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6b736964

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      435740      852923   814758329+  74  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 36) logical=(435739, 33, 45)
Partition 1 has different physical/logical endings:
     phys=(366, 104, 37) logical=(852922, 31, 29)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      340549      478536   269488144   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(107, 121, 32) logical=(340548, 59, 47)
Partition 2 has different physical/logical endings:
     phys=(10, 121, 13) logical=(478535, 44, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      137991      495994   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(137990, 7, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(495993, 58, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?     1001027     1001044       32672   bb  Boot Wizard hidden
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(65, 1, 0) logical=(1001026, 30, 55)
Partition 4 has different physical/logical endings:
     phys=(128, 0, 7) logical=(1001043, 13, 50)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02a546c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976762583+  ee  GPT



I dont really know what this means so more help is greatly appreciated!

---

### Post by linuxopjemac on 2010-05-08
I think /dev/sdc is your external ard drive, with 1 Tb of space. It's probably formatted in HFS+ with journaling under OSX. You can't write on such formats.

---

### Post by mackaframa85 on 2010-05-08
So, should I just go buy a cheap external drive and transfer the neccessary files and use it as my ubuntu drive :guitar:

If so, what recommendations if any on a cheap drive or another way to fully utilize my wubi environment.  I dont really want to do a triple boot.

---

### Post by P4man on 2010-05-09
AFAIK, ubuntu can write to HPS+ just fine. You may just not have permission to write there. press alt+F2 and type in:

```
gksudo nautilus
```

Find  the folder on the external drive you want to write to (probably in /media/nameoftheusbdrive). Right click the folder, properties, permissions. Make sure your user has permissions to write there. If you only need the folder from ubuntu, take ownership.

---

