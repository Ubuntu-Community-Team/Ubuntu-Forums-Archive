---
title: "adding a second hard drive to grub?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by carrizz on 2007-05-23
I have a 40gb hard drive with an existing installation of win xp which i have added as a second hard drive to my pc, can anyone tell me what i need to in order to add this device to grub so i can boot to it?

results of "fdisk -l"

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14084   113121697    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2   *       14084       23483    75505469    f  W95 Ext'd (LBA)
/dev/hda5           14084       14345     2104483+  82  Linux swap / Solaris
/dev/hda6           14346       15651    10490413+  83  Linux
/dev/hda7           15652       23483    62910508+  83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4998    40146403+   7  HPFS/NTFS

---

### Post by dstew on 2007-05-23
You need to add the following lines to the file /boot/grub/menu.lst```
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
chainloader +1
```
You can use the command nano to edit the file.```
sudo nano /boot/grub/menu.lst
```If that doesn't work, here is another variant for a Windows install on a second disk```
title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```If one of these works, please post to let me know. I am learning like everyone else. Thanks.

---

