---
title: "ubuntu 8.04 grub trouble"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by radiantarchon on 2007-12-30
i decided to be funny and mess around with hardy heron. when i installed hardy it had overwritten the menu.lst file. now windows xp is gone from the list. how do i get it back. i have only one hard drive and windows is on sda1.

---

### Post by overdrank on 2007-12-30
> **radiantarchon said:**
> i decided to be funny and mess around with hardy heron. when i installed hardy it had overwritten the menu.lst file. now windows xp is gone from the list. how do i get it back. i have only one hard drive and windows is on sda1.

Hi and could you post the output of the command ```
sudo fdisk -l
``` the is a L not a 1

---

### Post by radiantarchon on 2007-12-30
Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005cb79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8923    71673966    7  HPFS/NTFS
/dev/sda2   *        8924       11978    24539287+  83  Linux
archon@templar:~$

---

### Post by overdrank on 2007-12-30
> **radiantarchon said:**
> Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005cb79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8923    71673966    7  HPFS/NTFS
/dev/sda2   *        8924       11978    24539287+  83  Linux
archon@templar:~$

Whew I was glad to see the NTFS. Thought it might have installed over it. You can use the command to edit your grub ```
gksudo gedit /boot/grub/menu.lst
```
And this is a good link to add windows to the grub
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

### Post by radiantarchon on 2007-12-30
thanks

---

