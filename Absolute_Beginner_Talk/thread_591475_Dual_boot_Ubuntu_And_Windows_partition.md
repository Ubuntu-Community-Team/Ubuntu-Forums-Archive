---
title: "Dual boot Ubuntu And Windows partition"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Pabx on 2007-10-25
Well as i say in the title i want do dual boot widows and ubuntu, here is my menu.lst:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=39752567-e102-4092-b8e0-8caa051c55b5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=39752567-e102-4092-b8e0-8caa051c55b5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


What do i need to add?

if only one person dual booting with windows could help... post his menu.lst and i know what to do...

---

### Post by PPAAUULL on 2007-10-25
Here is what I got 


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4e662f1e-9cfa-4f96-b2c8-bbfa20ffad1f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4e662f1e-9cfa-4f96-b2c8-bbfa20ffad1f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by Duck2006 on 2007-10-25
In the terminal type to see where your windoze

sudo fdisk -l

Post the output.

---

### Post by Pabx on 2007-10-25
> **Duck2006 said:**
> In the terminal type to see where your windoze

sudo fdisk -l

Post the output.

My windows its in /dev/sda3/

on hd(0,1)

---

### Post by Pabx on 2007-10-25
> **PPAAUULL said:**
> Here is what I got 


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4e662f1e-9cfa-4f96-b2c8-bbfa20ffad1f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4e662f1e-9cfa-4f96-b2c8-bbfa20ffad1f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

ok ill try using yours Changing my partition Thanks

---

