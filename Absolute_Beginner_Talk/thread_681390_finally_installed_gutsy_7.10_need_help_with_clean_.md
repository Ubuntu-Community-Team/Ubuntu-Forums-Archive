---
title: "finally installed gutsy 7.10 need help with clean up"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by megabyzus on 2008-01-28
I have successfully created a dual boot Gutsy 7.10/WinME machine (during install gparted indicated on sda3 and sda7/swap).   When I boot , however, grub shows the extra past failed installs (grub menu.lst below).  . I also have extra disk space taken over I suspect from my previous dual boot with ubuntu 5.10.  I want to get these extra gigs back too. (screenshot of gparted attached)..  I think these are sda2,5, and 6.  I tried deleting these using gparted but it asked me to umouont first and when i tried umount it said said you need to umount next higher number, etc, etc.  Couldn't unmount anything.  As you see I also have 'unallocated space listed in gparted for about 8 gig.  I want to get all these gigs back and make my disk continiuous.  again grub menu.lst below and gparted screenshots attached.  Thanks!

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a1a2af6d-965a-4e69-8e9e-3b7d26665e0e ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a1a2af6d-965a-4e69-8e9e-3b7d26665e0e ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
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
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, kernel 2.6.17-12-386 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=e44a1e3f-d3d1-4768-a408-77cfb2e45a0e ro quiet splash 
initrd		/boot/initrd.img-2.6.17-12-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, kernel 2.6.17-12-386 (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=e44a1e3f-d3d1-4768-a408-77cfb2e45a0e ro single 
initrd		/boot/initrd.img-2.6.17-12-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, kernel 2.6.15-29-386 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=e44a1e3f-d3d1-4768-a408-77cfb2e45a0e ro quiet splash 
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, kernel 2.6.15-29-386 (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=e44a1e3f-d3d1-4768-a408-77cfb2e45a0e ro single 
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, kernel 2.6.12-10-386 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=e44a1e3f-d3d1-4768-a408-77cfb2e45a0e ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=e44a1e3f-d3d1-4768-a408-77cfb2e45a0e ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, kernel 2.6.12-9-386 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=e44a1e3f-d3d1-4768-a408-77cfb2e45a0e ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=e44a1e3f-d3d1-4768-a408-77cfb2e45a0e ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by brettg on 2008-01-29
Not sure what you are asking for re grub, but, you can simply remove the entries for everything other than the two you need using a text editor.

As for the disks, you can use df -h to see all the drives that are currently mounted and then use gparted to delete the remainder.

Caveat Emptor: Deleting partitions is irreversable. If you remove the wrong partition, you will lose data. Make sure you are sure you are doing the right thing before you commit,

---

