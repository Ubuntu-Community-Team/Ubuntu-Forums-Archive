---
title: "grub problems plz help asap !!! :-s"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Deaia on 2007-10-09
I really need some help with my computer...because i've partitioned it as to have two opperating systems....
 
The first is windows xp...and the seccond linux ubuntu v.7

My probleme is that when booting....i get the menu from where i must choose between windows and linux.... when i choose windows, it starts loading...but then i get a blue screen error.... unmountable_boot_volume :((

---

### Post by skymera on 2007-10-09
o i dont think its a grub problem if windows starts to load.

unmountable_boot_volume

is the kernel entry 110% correct in GRUB?

this may help:

[http://support.microsoft.com/kb/297185](http://support.microsoft.com/kb/297185)

if you have the recovery disk

---

### Post by Deaia on 2007-10-09
how should the kernel entry look like?? :-"

the only back up of my sistem is an acronis image....of my whole system before i installed linux
should i use acronis...get back my old settings ...and then try again to install linux?

---

### Post by skymera on 2007-10-09
ok here is my grub:

not sure if your is different:

```


title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f2d16883-22a1-42a1-a144-5cfce8e2a4f8 ro splash rootflags=data=writeback vga=795
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f2d16883-22a1-42a1-a144-5cfce8e2a4f8 ro single rootflags=data=writeback
initrd          /boot/initrd.img-2.6.20-16-generic

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

```

right, now looking at that has baffled me!

what about that MS link i gave you? any use?

i used [code} fixboot [/code] when my windows was broke, it worked!
overwrote grub, but it worked!

---

### Post by Deaia on 2007-10-09
well...the ms info is usefull...just that the i'm not sure that my windows is the real thing....a friend gave it...anyway....but i'll try it just the same....and after that reinstall grub then...

oh yes... do you think the probleme is because i used partition magic to steal some memory from one of my windows partition?? it wasn't the primary one....just a secondary.... :confused:

---

### Post by skymera on 2007-10-09
try the fixboot thing

that will most defo work.

read through Google how to do... you dont want to go too far and reinstall XP

---

### Post by Deaia on 2007-10-09
in a ubuntu live cd....during instalation I partitioned the memory i had freed earlyer on in windows with partition manger... 

this is my grub

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

title           Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bf808007-132f-4416-bdcb-86ee80d66150 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bf808007-132f-4416-bdcb-86ee80d66150 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


N.b: i had the same problem when the info about microsoft winodows etc....was in the driver specificly to deparate the menu items from the debian ones.....

---

### Post by skymera on 2007-10-09
asd i said, grub is fine, if windows boots GRUB works.

but when loading windows, it fails. thats a problem in Windows.

the recovery CD will work.

read that MS link i posted earlier:wink:

good luck

---

### Post by Deaia on 2007-10-09
and if i don't have the cd's.....? :P ...could i just use the acronis image and start over? :-? or linux can't see acronis...

---

### Post by skymera on 2007-10-09
if you dont have the CD...ermm i dont know.s

sorry

---

