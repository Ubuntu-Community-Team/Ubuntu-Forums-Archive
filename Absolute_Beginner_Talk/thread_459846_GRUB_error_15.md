---
title: "GRUB error 15"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2007-05-31
i got dual boot ubuntu and xp

I got this error message when i try to boot ubuntu at GRUB,
```

Error 15 : File not found
```

this is my /boot/grub/menu.lst
```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2164c960-39cb-418a-b5ba-3e6b25d3ff1d ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2164c960-39cb-418a-b5ba-3e6b25d3ff1d ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

this is my fdisk -l
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3570    28675993+   7  HPFS/NTFS
/dev/sda2            3571        4990    11406150    f  W95 Ext'd (LBA)
/dev/sda3   *        4991        7231    18000832+  83  Linux
/dev/sda4            7232        7239       60000   83  Linux
/dev/sda5            3571        4886    10570738+   7  HPFS/NTFS
/dev/sda6            4887        4990      835348+  82  Linux swap / Solaris

```

---

### Post by candtalan on 2007-05-31
(Please Note I am not any expert on this)

the following suggests /dev/sda4

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,3)

(because hd0 is first drive sda
and (hd0,3) is the fourth partiton on first drive.

However, 
/dev/sda3   *        4991        7231    18000832+  83  Linux
suggests that /dev/sda3 is marked  for boot

1) I hope I am correct
2) hope it helps!

---

### Post by oliviacond on 2007-05-31
problem solved after i change this line:
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,3)

```
to
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,2)

```

thanks for your post, i messed up with the partitions.

---

