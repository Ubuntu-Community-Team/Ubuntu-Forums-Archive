---
title: "Grub Error 17."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by AmbigFish on 2007-05-28
I tried help in a different part of the forum, but not many people apparently frequent there. I need some help fixing the Error 17. I already have all the information for you.

Here is what my sudo fdisk -l says:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         509     4088511   12  Compaq diagnostics
/dev/sda2   *         510        7519    56307825    c  W95 FAT32 (LBA)
/dev/sda3            7520       14462    55769647+  83  Linux
/dev/sda4           14463       14593     1052257+  82  Linux swap / Solaris

```

Here is what my blkid says:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         509     4088511   12  Compaq diagnostics
/dev/sda2   *         510        7519    56307825    c  W95 FAT32 (LBA)
/dev/sda3            7520       14462    55769647+  83  Linux
/dev/sda4           14463       14593     1052257+  82  Linux swap / Solaris

```

my fstab is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=4ae98113-c8bc-49cb-b934-64e4c5ec62d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0E4E-05CE  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=320D-180E  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=1aaa508e-1abd-4956-a32c-0eeaeaebf150 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/swapfile1 swap swap defaults 0 0
```

Here is my mtab:

```
/dev/sda4 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```

here is my menu.lst in my /boot/grub.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
"menu.lst" 167L, 4649C                                        1,1           Top


```

Please, help me.

---

### Post by AmbigFish on 2007-05-28
Bump. Only one person has looked at it... I really need help.

---

### Post by AmbigFish on 2007-05-28
oops. I guess this is what you guys would want for my menu.lst:

```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4ae98113-c8bc-49cb-b934-64e4c5ec62d4 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4ae98113-c8bc-49cb-b934-64e4c5ec62d4 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

---

### Post by pauljwells on 2007-05-28
I have the same problem. Take a look at this thread,  post #10, it looks the best fix.

[http://ubuntuforums.org/showthread.php?t=456959](http://ubuntuforums.org/showthread.php?t=456959)

---

### Post by AmbigFish on 2007-05-28
I decided to just format the stupid thing. I needed to anyway.

---

