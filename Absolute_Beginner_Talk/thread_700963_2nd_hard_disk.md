---
title: "2nd hard disk"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by buflodred on 2008-02-18
I have used the following commands to see my 2nd hard drive: sudo fdisk -lu, my 2nd drive shows up "Disk /dev/sdb: 80.0 GB", but I also see "Disk /dev/sdb doesn't contain a valid partition table"
The total result looks like this

 "Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007d822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    37608164    18804051   83  Linux
/dev/sda2        37608165    39102209      747022+   5  Extended
/dev/sda5        37608228    39102209      746991   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


How do I partition my 80 gb sdb drive ?

---

### Post by lgcabarcas on 2008-02-18
you could try to install Gnome-partition-manager from add/remove programs or synaptic, the program has a GUI which is pretty straight forward for what you're trying to do

---

