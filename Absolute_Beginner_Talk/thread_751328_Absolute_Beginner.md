---
title: "Absolute Beginner"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by robintoal on 2008-04-10
friends, I have preciously received help on here when I could not mount my external hard drive, that was initially solved with the "sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force" command. However this no longer works, I only tried it twice a week or so ago, and now I get a message stating "Failed to access '/dev/sdb1': No such file or directory"

Also when I hook up my horrible chinese usb drive it recognises and mounts, and even plays, but insists that the disk is already full when I try to add anything, but it's patently not. Any suggestions? RT

---

### Post by Fate Reconciled on 2008-04-10
Sure it's not /dev/sda1 you're looking for?

---

### Post by robintoal on 2008-04-10
In what context sorry. I tried switching the bits you suggested but i'm told their is no file or directory. RT

---

### Post by smurphy_it on 2008-04-10
post the output of the following command:

fdisk -l

(that's a lowercase L)

---

### Post by robintoal on 2008-04-10
Disk /dev/sdf: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dc90dc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        4864    39070048+   7  HPFS/NTFS

This is the disk that I am trying to mount.

---

### Post by smurphy_it on 2008-04-10
Try sudo mount -t ntfs-3g /dev/sdf1 /media/disk -o force

---

### Post by MrFSL on 2008-04-10
Do not double post PLEASE:

See answer posted here:
[http://ubuntuforums.org/showthread.php?p=4691081#post4691081](http://ubuntuforums.org/showthread.php?p=4691081#post4691081)

---

