---
title: "Lost NTFS partition folders"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by michaelof36 on 2007-04-29
I have Windows XP MCE partitioned on the same hdd as my Ubuntu installation. I also have a second hdd formatted in ntfs also which contains all my music. I wanted to be able to write to these partitions from within Feisty and also write to my flash drive (ntfs also). So I installed the NTFS Configuration Tool and now both of my folders that were on the desktop that displayed the contents of these ntfs partitions as well as my 2nd hdd are no gone and inaccessible. Where did they go and how can I get them back to the way they were?

---

### Post by AlexenderReez on 2007-04-29
check your partition


> sudo fdisk -l

then

 have you done this? --> under application --> systems tools --> NTFS configuration --> check both box

it suppose appears as normal....have a look at computer...there is suppose it will show you all of your partition......

---

### Post by michaelof36 on 2007-04-29
when i enter sudo fdisk -l, i get:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18470   148360243+   7  HPFS/NTFS
/dev/sda2           18471       28982    84437640   83  Linux
/dev/sda3           28983       30401    11398117+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

```

Also I have made sure and check both boxes and nothing comes up they are still inaccessible.

Any suggestions?

---

### Post by AlexenderReez on 2007-04-29
> gconf-editor


apps --> nautilus ---> check the desktop on the bottom right click it  "volumes visible"

have you restart after done those configuration ? ( normally it is better restart even not necessary )

---

