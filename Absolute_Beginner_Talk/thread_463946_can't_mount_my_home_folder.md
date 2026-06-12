---
title: "can't mount my home folder"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by benner on 2007-06-04
i have a 64-bit ubuntu feisty running on one hard disk (sda1) and i have a separate hard disk where i just did a fresh install of a 32-bit ubuntu feisty.  the drive is about 80 gigs and i partitioned it into a 30 and 50.  i put the OS on the 30 and the home folder on the 50 as suggested somewhere i read.  this way, if i have a problem, i can reinstall the OS and not lose my stuff.  anyways, when i boot into it, i have a few problems.  first, i get a command prompts telling me that 'apt-get is not installed' and then i get the root prompt with no gui.  i 'ctl+alt+del' and then it boots into the gui.  but then, it tells me that the /home doesn't exist and do i want to temporarily create a home folder in / so that i can boot up.  i say yes and then i get another error saying that my login lasted less than 10 seconds and something or other.  i didn't get the whole thing.  it crashes every time.  from the grub menu, i have no trouble booting into the 64-bit one.  and when i do, every partition on either drive appears.  So i am now logged into the 64 and looked at the grub and fstab in the 32-bit partition for clues.  i think i may have grub on both hard disks but don't know how to tell.  when i set the bios to boot from one disk, it goes straight into the 64 bit system with no options.  when i set it to boot from the other hard disk, i get the options to boot into either system, memtest and so on but the new 32 doesn't work as described above.

here's the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e6b6b851-322f-492c-ad90-c00af053b23b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb2
UUID=7a093602-667e-40bc-b35b-c6e861dc525e /home           ext3    defaults        0       2
# /dev/sda1
UUID=8cbfd813-b3b3-4a25-81b4-0fbcec8b415d /media/sda1     ext3    defaults        0       2
# /dev/sda3
UUID=4e46ea7d-ac0f-4e84-906e-0ac0133a2b2b /media/sda3     ext3    defaults        0       2
# /dev/sda4
UUID=6bc49198-c87e-4e5c-bc72-d8a5f076bd40 /media/sda4     ext3    defaults        0       2
# /dev/sda5
UUID=418dd4b8-ab5a-4ba7-b414-419389268988 none            swap    sw              0       0
# /dev/sda6
UUID=a1e67949-9d93-4261-9752-5aee5b6ce174 none            swap    sw              0       0
# /dev/sda7
UUID=55a1e652-495b-43d2-b164-c848a6fa4f71 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0

and here's the grub:


title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6b6b851-322f-492c-ad90-c00af053b23b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6b6b851-322f-492c-ad90-c00af053b23b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8cbfd813-b3b3-4a25-81b4-0fbcec8b415d ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8cbfd813-b3b3-4a25-81b4-0fbcec8b415d ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8cbfd813-b3b3-4a25-81b4-0fbcec8b415d ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8cbfd813-b3b3-4a25-81b4-0fbcec8b415d ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu, memtest86+ (on /dev/sda1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

any suggestions are appreciated.  thanks in advance...

---

### Post by taurus on 2007-06-04
How about the output of 

```
sudo fdisk -l
```

---

### Post by benner on 2007-06-04
here it is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14870   119443243+  83  Linux
/dev/sda2           29341       30401     8522482+   5  Extended
/dev/sda3           14871       22238    59183460   83  Linux
/dev/sda4   *       22239       29340    57046815   83  Linux
/dev/sda5           30027       30401     3012156   82  Linux swap / Solaris
/dev/sda6           29649       30026     3036222   82  Linux swap / Solaris
/dev/sda7           29341       29648     2473947   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3952    31744408+  83  Linux
/dev/hdb2            3953       10011    48668917+  83  Linux

---

### Post by benner on 2007-06-04
...asked me for my fdisk and then nothing?  I feel like a date stood me up.  Can anyone help me here?

---

### Post by benner on 2007-06-05
i got it sorted.  it was the fstab.  the next time you see a post where a noob asks for the 10 most important things to learn right away when switching to linux, you may want to suggest learning how fstab and grub work.  here are the webpages that i used:

[http://www.tuxmachines.org/node/16701](http://www.tuxmachines.org/node/16701)
for grub 

and

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
for fstab.

---

