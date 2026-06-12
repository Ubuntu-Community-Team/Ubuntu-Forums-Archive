---
title: "Boot FreeBSD from GRUB"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by valos on 2007-09-01
Hi,

I have two SATA hard drives on my machine, on the first one I have WinXP and Ubuntu 7.04 and I have installed PC BSD on the first partition of the second one.

I did not install the boot loader for PC BSD because I want to boot it from GRUB.

What changes do I have to do to GRUB config files in order to be able boot PC BSD?

From Ubuntu i did a fdisk -l:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482528+  a5  FreeBSD
Partition 1 does not end on cylinder boundary.
/dev/sda2            2551        5100    20482875    6  FAT16
/dev/sda3            5101        9689    36861142+   6  FAT16
/dev/sda4            9690       10011     2586465    6  FAT16

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
240 heads, 63 sectors/track, 51681 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13545   102400168+   7  HPFS/NTFS
/dev/sdb2           13546       46053   245760480    7  HPFS/NTFS
/dev/sdb3           46054       48627    19459440   83  Linux
/dev/sdb4           48628       51681    23088209    f  W95 Ext'd (LBA)
/dev/sdb5           48628       51404    20994088+   6  FAT16
/dev/sdb6           51405       51681     2094088+  82  Linux swap / Solaris

And this is grub's config file:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7b09c105-9ad5-4e2d-b90d-1ffc113f4344 ro quiet splash noapic nolapic pci=assign-busses
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7b09c105-9ad5-4e2d-b90d-1ffc113f4344 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7b09c105-9ad5-4e2d-b90d-1ffc113f4344 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7b09c105-9ad5-4e2d-b90d-1ffc113f4344 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Thanks.

---

### Post by jamvegan on 2007-09-01
I'm not certain about this, because I'm puzzled by the fact that fdisk thinks that Ubuntu is on the second drive and grub thinks that it's on the first, but if your grub configuration is working as you posted it, then I think that the entry you want to add to menu.lst is:
```
title PC BSD
root (hd1,a)
kernel /boot/loader
```

---

