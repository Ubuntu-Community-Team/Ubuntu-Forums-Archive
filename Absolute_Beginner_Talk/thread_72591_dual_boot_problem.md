---
title: ":::dual boot problem:::"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by crackity on 2005-10-06
I get "error23: error while parsing number" when I try to boot win xp.

fdisk -l

```
Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5690    45704893+   c  W95 FAT32 (LBA)
/dev/hda2            5691        7299    12924292+   f  W95 Ext'd (LBA)
/dev/hda5            5691        5754      514017   82  Linux swap / Solaris
/dev/hda6            5755        7299    12410181   83  Linux

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9964    80035798+   7  HPFS/NTFS
root@converge:/home/crackity #

```

grub menu :
```
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(sd1,0)
savedefault
makeactive
chainloader	+1

```



Thanks....

---

### Post by mark on 2005-10-06
Not sure, but I think the XP grub line should be:

root		(sd0,0)

instead of:

root		(sd1,0)

grub indexes on 0, not 1 - note that your Ubuntu kernel roots to (hd0,5), not (hd1,5).  See if changing that line helps.

Mark

---

### Post by SilentCacophony on 2005-10-06
Is that a SATA or SCSI drive? AFAIK, grub does not deal with sdX,X, only hdX,X (should be hd1,0 in this case, I think.)

Also, WinXP being on the second drive, I'd think it'd need to be mapped around to work.

You may want to back up the menu file first:

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup**

And try replacing the Windows XP section with this:

```
title Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1
```

---

### Post by crackity on 2005-10-07
thanks alot, that solved the problem;-)

---

