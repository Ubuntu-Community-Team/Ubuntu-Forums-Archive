---
title: "Windows XP entry disappeared from grub menu"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-10-18
Hi everyone, I'm not sure how this happened but I can't boot into windows for the moment (mind you I only want to try out the UT3 demo). I found similar threads so I will post the output of sudo fdisk -l:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12158    97659103+  83  Linux
/dev/sda2           12159       12407     2000092+  82  Linux swap / Solaris
/dev/sda3   *       12408       19456    56621092+   7  HPFS/NTFS



and of /boot/grub/menu.lst, minus the comments at the top (unless those are needed to see what's up?)


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1fd967f0-21e8-49ac-849f-55e036055238 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1fd967f0-21e8-49ac-849f-55e036055238 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1fd967f0-21e8-49ac-849f-55e036055238 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1fd967f0-21e8-49ac-849f-55e036055238 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


What do I need to do to get back into windows so I can mess with UT3 while I wait for 7.10 to become available?:)

Thanks.

---

### Post by mozetti on 2007-10-18
See if there is a backup copy of the /etc/grub/menu.lst file -- depending on how GRUB got updated, it should make a backup copy of the old menu.lst file.

If there's one there, just copy the relevant lines from the backup. If that doesn't work, I know there's info here on the forum about the proper way to add the required lines of code. The GRUB help online has the info, too. Or maybe 'man grub' or check the link in my sig for man pages online.

---

### Post by mikeyphi on 2007-10-18
If you don't find a backup copy of menu.lst:-
here is the final bit of mine:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

