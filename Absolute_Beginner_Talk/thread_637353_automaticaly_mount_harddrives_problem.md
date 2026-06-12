---
title: "automaticaly mount harddrives problem"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Balvinder25 on 2007-12-10
hi all,
         i use 7.04 and would like to know how to mount my windows partitions automatically..These partitions do show up in Computer but i have to click on it the hdd ..then enter the root password and then im able to access these hdds...??so could anyone help me out on this..

---

### Post by taurus on 2007-12-10
What partitions are those?  Post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l  <-- lower case letter l, not number 1
```

---

### Post by Balvinder25 on 2007-12-10
hi following is the fdisk -l report tht u asked for..

Disk /dev/sda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         510     4096543+   b  W95 FAT32
/dev/sda2             511        2877    19012927+   f  W95 Ext'd (LBA)
/dev/sda3   *        2878        4963    16755795   83  Linux
/dev/sda5             511        1673     9341766    7  HPFS/NTFS
/dev/sda6            1674        2784     8924076    b  W95 FAT32
/dev/sda7            2785        2877      746991   82  Linux swap / Solaris

regards.
by the ...i dont have to type my root password but i have to double click on the drives to mount them.once..then onwards im able to use them//

thanks aton..
:guitar:

---

