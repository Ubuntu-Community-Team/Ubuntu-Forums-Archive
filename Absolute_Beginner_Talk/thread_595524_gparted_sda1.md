---
title: "gparted sda1"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by castep_nut on 2007-10-28
Strange problem using gparted livecd. Have loaded from CD so none of the partitions (eg sda1) are mounted, which should allow me to expand sda1 into unmounted volume space.

However, upon pressing the resize button, the maximum size is still limited to the previous size - it will not allow me to expand into the unmounted partition. There seems to be some sort of a small block (logical partition) stopping the expansion into the other partition. 

Any help would be appreciated. Thanks, CN.

---

### Post by p_quarles on 2007-10-29
It's hard to say without more information. Can you type the following (from your normal Linux installation, not the Gparted live CD) in a terminal, and report the output?
```
sudo fdisk -l
```

---

### Post by castep_nut on 2007-10-29
The output is: (sda1 is what I would like to extend into an unmounted volume, sda2 is a strange small portion, sda3 is another mounted disk). Cheers

Disk /dev/sda: 16.1 GB, 16106127360 bytes
255 heads, 63 sectors/track, 1958 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         492     3951958+  83  Linux
/dev/sda2             493         522      240975    5  Extended
/dev/sda3             523        1305     6289447+  83  Linux

---

### Post by castep_nut on 2007-10-31
Problem now solved. Thanks

---

