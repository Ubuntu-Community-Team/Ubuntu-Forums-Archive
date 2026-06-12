---
title: "Kubuntu fail to boot after installing PCLinuxOS"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by CalvinChile on 2007-09-14
Hi, maybe someone can help me:

I had WindowsXP and Kubuntu 7.04 installed in my Inspiron. Then I decided to get rid of Windows and installed PCLinuxOS instead. After the installation I'm not able to boot into Kubuntu.

Can somebody have a look into the grub menu.lst for both Kubuntu and PCLinux and tell me what is wrong.

Thanks a lot,
Calvin

Here is the result from fdisk -l  

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda2            3193        9284    48933990   83  Linux
/dev/sda3               1        9546    76678213+   5  Extended
/dev/sda5               1        1019     8185054+  83  Linux
/dev/sda6            9285        9546     2104483+  82  Linux swap / Solaris
/dev/sda7            1020        1528     4088511   82  Linux swap / Solaris
/dev/sda8            1529        3192    13366048+  83  Linux

Partition table entries are not in disk order

sda2 is where Kubuntu is installed and sda6 is its swap partition. PCLinuxOS is installed on sda5 (/)  sda7 (swap) and sda8 (/home)

The menu.lst on PCLinuxOS is:
======================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda5  acpi=on resume=/dev
/sda7 splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda5  acpi=on resum
e=/dev/sda7
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda5  failsafe acpi=on
 resume=/dev/sda7
initrd (hd0,4)/boot/initrd.img

title Kubuntu
root (hd0,1)
kernel  (hd0,1)/boot/vmlinuz-2.6.20-16-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro single
initrd  (hd0,1)/boot/initrd.img-2.6.20-16-generic


and the menu.lst that I found in Kubuntu menu.lst is:
======================================
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro single
initrd          /boot/initrd.img-2.6.17-11-generic

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by bwhitaker on 2007-09-14
Maybe Change:
```

title Kubuntu
root (hd0,1)
kernel (hd0,1)/boot/vmlinuz-2.6.20-16-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro single
initrd (hd0,1)/boot/initrd.img-2.6.20-16-generic

```

to 

```

title Kubuntu
root (hd0,1)
kernel (hd0,1)/boot/vmlinuz-2.6.20-16-generic root=UUID=66185b49-3ab3-4ed4-82b
4-6901ab045707 ro single
initrd /boot/initrd.img-2.6.20-16-generic

```

Or it's possible the drive uuids are different

Check
```

$ blkid

```
and see if your entry for /dev/sda2 has the uuid 66185b49-3ab3-4ed4-82b
4-6901ab045707

If it isn't change your menu.lst entry(the top one) to 
```

title Kubuntu
root (hd0,1)
kernel (hd0,1)/boot/vmlinuz-2.6.20-16-generic root=/dev/sda2 ro single
initrd /boot/initrd.img-2.6.20-16-generic

```

---

### Post by CalvinChile on 2007-09-14
Thanks for the reply! I will try the changes.

The blkid for sda2 is the same one I have in the menu.lst 

Right now I will try the change yu propose to the menu.lst

---

### Post by CalvinChile on 2007-09-14
Hi,

After the change you propose, the system started to boot in Kubuntu but after a while the console messages stopped comming and then I got th following message:

[I]Check root=bootar cat /proc/cmdline 
or missing modules, devices:cat /proc/modules ls /dev

ALERT /dev/disk/by-uuid/66185b49-.......   does not exist  droping to shell!!
[/I]
and then I have a promp *(inittramfs)*

Any idea?

---

