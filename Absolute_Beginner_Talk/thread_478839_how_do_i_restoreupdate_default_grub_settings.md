---
title: "how do i restore/update default grub settings?"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by jklslvch on 2007-06-19
hey i just did some stuff with my partitions (moved them around and installed a different distro) and now when grub starts it cant find the boot files anymore

how can i like "update" my grub settings from the Live CD

---

### Post by Happy_Man on 2007-06-19
Boot the live CD, open the terminal, and mount the partition that has / on it. Eg, if it was on /dev/sda1.....```
sudo mkdir /media/Ubuntu
sudo mount /dev/sda1 /media/Ubuntu
```

Then go to the /boot/grub/menu.lst file (or in this case, /media/Ubuntu/boot/grub/menu.lst) and edit to your taste.

---

### Post by jklslvch on 2007-06-19
> **Happy_Man said:**
> Boot the live CD, open the terminal, and mount the partition that has / on it. Eg, if it was on /dev/sda1.....```
sudo mkdir /media/Ubuntu
sudo mount /dev/sda1 /media/Ubuntu
```

Then go to the /boot/grub/menu.lst file (or in this case, /media/Ubuntu/boot/grub/menu.lst) and edit to your taste.

my other partitions dont even come out
and the partition that ubuntu was on changed (it was on /dev/hda5 but now it must be /hda6)

---

### Post by Happy_Man on 2007-06-19
What's the output of the command ```
sudo fdisk -l
```?

---

### Post by jklslvch on 2007-06-19
> **Happy_Man said:**
> What's the output of the command ```
sudo fdisk -l
```?

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2551    20490876    7  HPFS/NTFS
/dev/hdc2            2552        9733    57689415    f  W95 Ext'd (LBA)
/dev/hdc5            2552        8884    50869791    7  HPFS/NTFS
/dev/hdc6            8885        9733     6819561    7  HPFS/NTFS

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2450    19679593+   c  W95 FAT32 (LBA)
/dev/hdd2            2451        4865    19398487+   f  W95 Ext'd (LBA)
/dev/hdd5            2451        2451        8001    1  FAT12
/dev/hdd6            2452        2517      530113+  82  Linux swap / Solaris
/dev/hdd7            2518        3297     6265318+  83  Linux
/dev/hdd8            3298        4081     6297448+  83  Linux
/dev/hdd9            4082        4865     6297448+  83  Linux
ubuntu@ubuntu:~$



and my device.map file in the grub folder has this 

(hd0)	/dev/hdc
(hd1)	/dev/hdd

i think ubuntus on /dev/hdd9

---

### Post by orb9220 on 2007-06-19
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

