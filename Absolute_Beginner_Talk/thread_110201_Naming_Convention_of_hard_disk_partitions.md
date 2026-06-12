---
title: "Naming Convention of hard disk partitions"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2005-12-30
Hello everybody!

My knowledge in Linux OS is very limited and hence this question may seem silly.  
In the following line I need to replace hd0,1 with my Ubuntu boot partition.

splashimage (hd0,1)/boot/grub/images/ubuntu.xpm.gz

The output of the command sudo fdisk -l is as follows:

vijay@ufonix1:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1211     9727326    7  HPFS/NTFS
/dev/hda2            1212        2388     9454252+  83  Linux
/dev/hda3            2389        2434      369495    5  Extended
/dev/hda5            2389        2434      369463+  82  Linux swap / Solaris

Is the location of my Ubuntu boot partition is same as hd0,1 or different.  Please help!

Thanks in advance.

**And a very happy new year to all!!!**

---

### Post by steve.horsley on 2005-12-30
(hd0,1) is grub's naming convention for the first hard disk, second partition (Grub numbers them starting from 0). Linux's name for the same partition would be hda2 (Linux numbers them starting from a and 1), which would appear to be you Ubuntu root partition.

Hope this is what you were looking for.
Steve

---

### Post by gmerritt on 2005-12-30
I'm assuming you are already in /boot/grub/menu.lst , so just look for an entry that looks like the following:
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro vga=771 quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

In this case it would be (hd0,2).
Hope this helps.
Happy New Year:)

---

