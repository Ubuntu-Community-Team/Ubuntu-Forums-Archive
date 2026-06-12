---
title: "grub error 17 with xp/feisty dual boot"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by afflusso on 2007-06-13
I have a dual boot between ubuntu and XP. I'm pretty sure my windows data is intact after installing feisty over it. I have a partition for XP, one for ubuntu, and one fat32, plus the swap. I think it should be working, except the grub error comes up when I boot the computer.

I had grub working previously, but then I reinstalled it while keeping the same XP install, and adding the fat32, and now grub doesn't load (and nothing else).

What might be the problem? If there is anything I should do from the live cd to diagnose the problem or help us figure it out, tell me what I should try.

This is a topic of mine from yesterday that might have some more information if I'm not clear enough: [http://ubuntuforums.org/showthread.php?t=472057](http://ubuntuforums.org/showthread.php?t=472057)

---

### Post by Inxsible on 2007-06-13
Boot up with a LiveCD and open a terminal and post back the out put of the following command

```
sudo fdisk -l
``` -l is lowercase L

---

### Post by afflusso on 2007-06-13
Here is the result:

[B]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3966    31856863+   7  HPFS/NTFS
/dev/sda2            3967        6822    22940820    b  W95 FAT32
/dev/sda3            6823        9729    23350477+   5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sda6            6823        9541    21840304+   b  W95 FAT32

Partition table entries are not in disk order

[/B]

---

### Post by Inxsible on 2007-06-13
> **afflusso said:**
> Here is the result:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3966    31856863+   7  HPFS/NTFS
/dev/sda2            3967        6822    22940820    b  W95 FAT32
/dev/sda3            6823        9729    23350477+   5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sda6            6823        9541    21840304+   b  W95 FAT32

Partition table entries are not in disk order



There you have it !! 
You seem to have lost your Linux install and with it your GRUB
You seem to have formatted your Linux install to FAT32 -- specifically check /dev/sda6 which is a logical partition within /dev/sda3.

You now have 2 FAT32 drives

---

### Post by afflusso on 2007-06-13
here is a screenshot of gparted. it looks like sda2 is ext3. I'm not sure how two fat32's were created.

Does this mean the ubuntu install failed? I wouldn't mind reinstalling it as long as my NTFS is intact.

What should I do now to get grub working again?

---

### Post by afflusso on 2007-06-13
Under gparted, whenever I select a partition, it says that none of them is mounted. I also can't resize any of them like I could before.

Does anyone know how to solve the problem with grub (if it is just grub)?

---

### Post by Inxsible on 2007-06-13
If you are not averse to re-installing, then you should re-install in the correct partition. Be careful of what you select in your choices. It does seem weird that fdisk showed sda2 as FAT32 and GParted shows it to be ext3 :confused:

---

### Post by afflusso on 2007-06-13
I started the installer and it is showing sda2 as ext3. I too can't figure out why it shows as fat32 under fdisk. I'll try to get the install going.

---

### Post by afflusso on 2007-06-13
Ugh! this is exactly what happened last time: it got to about 94% and it says: Unable to install grub in (hd0).
Executing grub-install failed. This is a fatal error.

Do you think I entered some parameter wrong during installation? What could be causing this?

---

### Post by antoz on 2007-06-14
Sorry to see you are still having problems with your install. I don't really know enough to give any good advice how to fix grub or to explain the cause. If it has not installed it is possible to do it after, or maybe you need to edit your menu lst, if grub is in your linux install it would reside in hd1, hd0 is your window partition. Maybe someone else has some answers for you, there is a lot of info about grub in this link [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

