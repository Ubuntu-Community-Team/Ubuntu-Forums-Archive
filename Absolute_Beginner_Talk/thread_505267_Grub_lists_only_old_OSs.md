---
title: "Grub lists only old OSs"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by mikeb on 2007-07-20
After reformatting my Windows partition, I followed instructions here to be sure that Grub was still installed in the MBR. Everything seemed to be fine. However, when I actually restarted, Grub did indeed appear, but only listed older versions of Ubuntu and Windows (which no longer exists).

When I booted into an older version of Ubuntu (6.06), I was able to see the former Windows partition and the new Ubuntu partition, but both gave an error when I tried to mount them.

I then rebooted using the install disk and I was then able to mount the new Ubuntu and former Windows partition.

How can I make Grub list and boot into the new version of Ubuntu?

---

### Post by tomcheng76 on 2007-07-20
please post the following things

1. cat /boot/grub/menu.lst

2. sudo fdisk -l

3. cat /etc/fstab

---

### Post by mikeb on 2007-07-20
Thanks for the reply. Here are the results you requested:


```


**cat /boot/grub/menu.lst**
title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

**sudo fdisk -l**

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12978   104245753+  83  Linux
/dev/hda2           12979       18636    45447885   83  Linux
/dev/hda3           23970       24321     2827440    5  Extended
/dev/hda4           18637       23969    42837322+  83  Linux
/dev/hda5           24146       24321     1413688+  82  Linux swap / Solaris
/dev/hda6           23970       24145     1413657   82  Linux swap / Solaris

Partition table entries are not in disk order
[B]
cat/etc/fstab[/B]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


FYI, the new Ubuntu version is on /dev/hda4

---

### Post by mikeb on 2007-07-20
bump.

---

