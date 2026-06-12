---
title: "Updated kernel image doesn't show up in grub"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Lystrodom on 2007-02-10
I'm running Edgy, and I just recently updated from 2.6.17-10 generic to 2.6.17-11 generic. The only problem is that the new image doesn't appear in grub, only one that shows up is -10. I found grub's menu.lst, and it listed both -10 and -11, but when actually booting, only -10 shows up.

If it makes any difference, I have three hard drives. Edgy is on the SATA drive, Dapper 64bit version is on a second hard drive, and Windows XP Pro is on a third hard drive. Both the second and third hard drives are regular ATA.

Any help would be greatly appreciated.

---

### Post by Lystrodom on 2007-02-10
Bump?

---

### Post by jordanmthomas on 2007-02-10
Can you show us the output of:
```
ls /boot/
```
and
```
cat /boot/grub/menu.lst
```

---

### Post by Lystrodom on 2007-02-10
Sure thing.

```
ls /boot/
abi-2.6.17-10-generic         initrd.img-2.6.17-11-generic
abi-2.6.17-11-generic         memtest86+.bin
config-2.6.17-10-generic      System.map-2.6.17-10-generic
config-2.6.17-11-generic      System.map-2.6.17-11-generic
grub                          vmlinuz-2.6.17-10-generic
initrd.img-2.6.17-10-generic  vmlinuz-2.6.17-11-generic


```


```

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet
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


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, kernel 2.6.15-27-386 (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash 
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, kernel 2.6.15-27-386 (recovery mode) (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single 
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, kernel 2.6.15-23-386 (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash 
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single 
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, memtest86+ (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, kernel 2.6.15-23-386 (on /dev/sda1) (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash 
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sda1) (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single 
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, memtest86+ (on /dev/sda1) (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title           Ubuntu, memtest86+ (on /dev/hdb1) (on /dev/sda1) (on /dev/hdb1)
root            (hd1,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

```

That was minus the default options

---

### Post by Lystrodom on 2007-02-10
Oh, and 2.6.15-27 doesn't show up, either. Just -23.

---

### Post by jordanmthomas on 2007-02-10
weird...I can only see one thing that is strange.  I haven't seen quiet passed like this:
```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
[COLOR="Red"]quiet[/COLOR]
savedefault
boot

```
but it is done that way on 2.6.17-10 and that shows up and boots no problem, correct?  To make sure, try
```
uname -r
``` It should show 2.6.17-10-generic
I can't find your problem.  Maybe someone else will read this and be able to help.

---

### Post by Lystrodom on 2007-02-10
It does indeed spit out 2.6.17-10 generic.

Thanks anyway. Hopefully someone else will be able to help.

---

### Post by meborc on 2007-02-10
have you tried update-grub after you have made the changes to the grub menu list?

---

### Post by Lystrodom on 2007-02-10
Just tried that, it didn't help. That just updates the menu.lst, which had already been updated.

---

