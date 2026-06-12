---
title: "how do I get grub to regonize another bootable linux partition"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by coolcalt on 2008-04-10
I just installed an ubuntu installation to one of my other drives,   After fighting with grub I managed to get my old install to boot.  Great, I was hoping not to lose it.  I had installed my new installation to hd0, I looked in menu.lst and it dosnt contain an entry for my new install.  What's the best way to go about putting an entry there?  

I installed 8.04 there, do i have to reference its kernel version of which I wouldn't have a clue how to find.

Easy on me I"m new

---

### Post by coolcalt on 2008-04-10
my current menu.lst
> ## ## End Default Options ##
title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bd1fda3e-c70f-48da-89b6-eced5c3bab39 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bd1fda3e-c70f-48da-89b6-eced5c3bab39 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=bd1fda3e-c70f-48da-89b6-eced5c3bab39 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bd1fda3e-c70f-48da-89b6-eced5c3bab39 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bd1fda3e-c70f-48da-89b6-eced5c3bab39 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
chainloader     +1

---

### Post by Oldsoldier2003 on 2008-04-10
the easiest way is to use the [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/") to setup grub. alternatively you could just edit the grub menu.lst manually to show the entry  for your other install. here is a nice tutorial for multibooting: [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by coolcalt on 2008-04-10
Thank you, I'll try those suggestions

---

### Post by louieb on 2008-04-10
The easiest way for GRUB in one Linux installation to boot another  Linux installation is the **configfile or chainloader** option. 
Herman explains it well. just search his page for chainloader and that will show you how to set it up. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

