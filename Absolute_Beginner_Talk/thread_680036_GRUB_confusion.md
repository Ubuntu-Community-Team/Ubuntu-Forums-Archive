---
title: "GRUB confusion"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Cchhrriiss on 2008-01-27
So i know there are a lot of other topics about this but i seem to getting nowhere (or even taking a few steps back at this point.

I can't boot to my ubuntu partition anymore at all either through my normal grub menu or using ultimate boot disc.

I have two Sata drives and ubuntu is on my second.  When i try to boot using normal grub menu the system hangs and i get a blank curser at the top.  When using grub boot through ultimate boot disc i get error 13

here is the outcome of fdisc

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20317   153596488+   7  HPFS/NTFS
/dev/sda2           20318       25571    39720240    f  W95 Ext'd (LBA)
/dev/sda5           20318       25571    39720208+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004db19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1044     8385898+  82  Linux swap / Solaris
/dev/sdb2   *        1045       37517   292969372+  83  Linux

I used to have an ide drive that had grub on it...removed it to start my lamp server and that is when all the fun began.

Thanks for the help guys...all the other pages i look through just get me a little more confused as the problems are just a little different than mine and i really don't want to have to format my partition again as i just got my 64 bit working perfectly!!

---

### Post by dstew on 2008-01-27
When you boot your computer (without using super grub disk or ultimate boot disk) do you get the grub menu?

---

### Post by logos34 on 2008-01-27
If you are get the grub menu but it goes blank when you try to boot ubuntu selection, then it may be as simple as changing root.  If grub is on the windows drive and removing the IDE drive started all this, then maybe linux drive was seen as the third drive (hd2), but now it's second (hd1)...so you could try pressing 'e' on the ubuntu kernel on the grub screen, 'e' again on the 'root' line and change to (hd**1**,1).  Press 'enter' and 'b' to boot.  See if that gets you anywhere.

---

### Post by Cchhrriiss on 2008-01-27
I do get the grub menu With 3 different options...
ubuntu option (doesn't work  error 25 i think)
Windows xp (works)
another ubuntu boot option on what i belive it thinks still on my idee drive (doesn't work start to load but hangs on ubuntu load screen)
and a third ubuntu option (doesn't work same as the 1st option)

The only bootable partions i have on my drives are the windows xp and my 64bit ubuntu  each on seperate sata drives...


I will try and change the root from grub

---

### Post by Cchhrriiss on 2008-01-27
WEIRD!!
Ok i managed to boot to my ubuntu partition by editing the first option in grub to (hd0,1)
some weird things happened...ubuntu started to load and the crashed bringing me to a command line showing some random errors :(
well after trying some random stuff i pressed alt+ctrl+del and it booted up like normal after that....
so thanx for the help but i have some cleanup questions if anyone is willing to help...
1st y did that happen :)
second did Grub save my edit to the boot menu or do i have to try this every time?
man i just want a clean boot again and i am kinda nervous to mess with it unless i know what to do for fear of really screwing things up

---

### Post by logos34 on 2008-01-27
no, you have to edit menu.lst to make the change permanent:

gksudo gedit /boot/grub/menu.lst

change root and groot lines

So I guess grub is on sdb.

Post your menu.lst before you edit it, if you could.

---

### Post by Cchhrriiss on 2008-01-27
I think this is the part u wanted...thanks again

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=29f93ff9-a588-4b2d-a166-d7bbca89aa41 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=29f93ff9-a588-4b2d-a166-d7bbca89aa41 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hdd2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4e24d0f3-a025-4875-a9a2-9360e78e9745 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd2.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hdd2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4e24d0f3-a025-4875-a9a2-9360e78e9745 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd2.
title		Ubuntu 7.10, memtest86+ (on /dev/hdd2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb3)
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9ff18c97-0303-4542-be46-4bcb0a0349e7 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb3)
root		(hd2,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9ff18c97-0303-4542-be46-4bcb0a0349e7 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 7.10, memtest86+ (on /dev/sdb3)
root		(hd2,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by logos34 on 2008-01-27
I was right in thinking the ubuntu 7.10 gutsy install drive (sdb) was seen as third in order at install time (hd2,1), and the IDE was seen as first (makes sense--grub detects ide channels first).

So, if (hd0,1) works, then you're definitely booting from sdb.  So clean up menu.lst:

> title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=29f93ff9-a588-4b2d-a166-d7bbca89aa41 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=29f93ff9-a588-4b2d-a166-d7bbca89aa41 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

