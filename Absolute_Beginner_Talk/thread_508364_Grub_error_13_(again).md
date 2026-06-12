---
title: "Grub error 13 (again)"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by simo_mon on 2007-07-24
hi have been readng through the postings and general google info on grub error 13 messages.... but still have no change....

background... installed latest edition of ubuntu on my laptop was working fine with a dual boot windows xp...... closed the laptop without logging out/shut down.....  ubuntu crapped itself got it back up and running.... ok....
 
windows xp now not booting was error 13 ... read ... went in an edited the /boot/grub/menu.lst and checked out the order of the hard drives... looks as though xp should be on 0... but changed it to 1 anyway ...just changed the error to a type 12......

this is what fdisk shows

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25598128+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2            3187        6895    29785896+   f  W95 Ext'd (LBA)
/dev/sda5            3187        6835    29296875   83  Linux
/dev/sda6            6836        6895      481918+  82  Linux swap / Solaris

and this is what is in the menu.lst 

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c15f583e-ca18-40c8-ae72-f19be5bf4c3c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=c15f583e-ca18-40c8-ae72-f19be5bf4c3c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c15f583e-ca18-40c8-ae72-f19be5bf4c3c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c15f583e-ca18-40c8-ae72-f19be5bf4c3c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
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

would appreciate any ideas or links to info.....
both systems on the 1 physical drive (as above)

thanks

---

### Post by ReaderRat on 2007-07-24
[GRUB Error Codes](http://www.uruk.org/orig-grub/errors.html)

**Bump**

---

### Post by dstew on 2007-07-24
Does your Linux system boot OK? Do you get the grub error 13 only when trying to boot Windows?

---

### Post by simo_mon on 2007-07-27
thanks for the reply..
1st reply
 yeah have checked out definitions of error and have a reasonable understanding.....

2nd reply 

yeah ubuntu boots fine = no problems....

its just xp... is this because grub can't associate or find the files required for the  xp boot....??

thanks

---

