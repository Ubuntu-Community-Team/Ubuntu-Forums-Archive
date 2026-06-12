---
title: "intristing duel boot situation"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by darksidedude on 2007-08-16
I have two hard drive in my computer, ( 40 gig master 20 gig slave)
the master drive has my ubuntu installation ( with its own grub) the slave has a fedora 7 install on it ( with its own grub) when I want to boot fedora I unplug my ubuntu drive, and vice-versa

is there away to get only one bootloader and have it recoginise both, and not lose data

these installs are kinda old and thus have important data on them 

Thanks for the help

ps. sorry for spelling wrong =(

---

### Post by msubzwari on 2007-08-16
Short answer is YES.  

You can configure the grub loader on Master drive (ubuntu) to boot the Fedora OS via the menu.  All you need to do is modify the menu.lst file (located usually at /boot/grub/menu.lst)

You need to add the lines from Fedora grub file exactly to the grub file in Ubuntu.  Unfortunately, I am at work and cannot give you an example. I hope you got the idea of what to do.

---

### Post by darksidedude on 2007-08-16
Yea, I don't quite know what to add, my fedora drive does show up in ubuntu as /boot

so that confused me Thought it would be hdb5 ( or something not so complex):lolflag:

---

### Post by Inxsible on 2007-08-16
post your fstab and also your /boot/grub/menu.lst from the Ubuntu install

---

### Post by darksidedude on 2007-08-16
here is the fstab list

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4863     1630597+  82  Linux swap / Solaris

Disk /dev/hdb: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        2431    19422585   8e  Linux LVM

Disk /dev/sda: 1001 MB, 1001914368 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      978400+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(120, 254, 63) logical=(121, 206, 21)


here is the grub part
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8e5c3104-8607-4d1d-b2ab-136fa9c293b4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8e5c3104-8607-4d1d-b2ab-136fa9c293b4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8e5c3104-8607-4d1d-b2ab-136fa9c293b4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8e5c3104-8607-4d1d-b2ab-136fa9c293b4 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

---

