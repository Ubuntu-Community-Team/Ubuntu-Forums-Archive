---
title: "Removing my Windows disc"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by carrizz on 2008-02-08
Hi, I would like to remove my windows hard disc as I no longer need to duel boot. If I pysically remove the drive I can no longer boot into ubuntu, I get past grub but ubuntu hangs during start up. What changes do I have to make to my system in order to remove my windows drive?
Thanks,
C.

---

### Post by airbornemist6 on 2008-02-08
First of all, put the drive back in, and edit your menu.lst. Second, you'll need to set the bios to boot from your ubuntu drive, and then, you'll need to fix grub. There are plenty of threads about this if you don't mind using the search button.

---

### Post by forestpixie on 2008-02-08
can you post these first

sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab

---

### Post by carrizz on 2008-02-08
> **forestpixie said:**
> can you post these first

sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab

```

 fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x394695b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1304    10474348+  83  Linux
/dev/sda2            1305       30401   233721652+   5  Extended
/dev/sda5            1305        1813     4088511   82  Linux swap / Solaris
/dev/sda6            1814       30401   229633078+  83  Linux

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1dfb1df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4110    33013543+   7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb2dfb2df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24415   196113456   83  Linux
/dev/sdc2           24416       24792     3028252+   5  Extended
/dev/sdc5           24416       24792     3028221   82  Linux swap / Solaris

cat /boot/grub/menu.lst


title           Linux Ubuntu, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Ubuntu, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sdc1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           linux (on /dev/sda1)
root            (hd2,0)
kernel          /boot/vmlinuz BOOT_IMAGE=linux root=/dev/hda1 acpi=on resume=/dev/hda5 splash=silent vga=788 
initrd          (hd2,0)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           linux-nonfb (on /dev/sda1)
root            (hd2,0)
kernel          /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/hda1 acpi=on resume=/dev/hda5 
initrd          (hd2,0)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           failsafe (on /dev/sda1)
root            (hd2,0)
kernel          /boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/hda1 failsafe acpi=on resume=/dev/hda5 
initrd          (hd2,0)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=5dc293b0-35db-41cf-94cd-7770df2d5cc0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=37ab4728-3945-9cbc-829f-9879aaeb0fce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       



```

---

### Post by forestpixie on 2008-02-08
all looks pretty normal to me - can you boot it to find out what is hanging

if airborne's bios thing worked - say so 

you can disbale quiet and splash and you'll get to see what's starting - make a note of what is causing it to hang

have a look here 

[https://answers.launchpad.net/ubuntu/+question/17235](https://answers.launchpad.net/ubuntu/+question/17235)

---

