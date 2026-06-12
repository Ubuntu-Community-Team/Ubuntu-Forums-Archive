---
title: "Ubuntu/RH Dual Boot Help"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by captainzingo on 2007-10-02
Hi, I know there must be a million threads on dual booting, GRUB, etc, but I'm having trouble wrapping my head around what must be so simple.

I have two HDDs, the primary master had Red Hat installed, I installed Ubuntu on the second.

Now, I can't boot to RH, but I can boot to Ubuntu from hda1 (hd0), though it's installed on hdb1 (hd1).  I messed around with GRUB for a while, and at this point, the settings to boot my second HDD (Ubuntu) are on my first HD.  I assume it's because I setup GRUB on both of my drives from within Ubuntu.   I tried restoring with Super Grub Disk, but this hasn't helped.

So, I assume I have to just have GRUB installed on hda1 (hd0) with options for both booting to hda1 and hdb1.  I think I'm almost there, I just have to edit the menu.lst and add the RH boot parameters.

My problem:  What are the RH boot parameters and how do I find this out?  I assume I need the vmlinuz, kernel, UUID lines, but I don't know the values.

tx

---

### Post by Duck2006 on 2007-10-02
Edit your menu.lst and add these lines

title "what you want to call it"
root (hd1,0)
chainloader +1

---

### Post by captainzingo on 2007-10-02
Well, here's where I am.

I have my BIOS set to boot to my first drive (HDD-0).

This boots to my grub menu (see below).

At this point, the first option in my menu.lst works, booting to (hd1,0), but I can't boot to (hd0,0) using the entry I added at the bottom with chainloader +1.  I get an "invalid executable" error.



## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7e22f10f-71c4-4aab-8257-1625c6546ed7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7e22f10f-71c4-4aab-8257-1625c6546ed7 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7e22f10f-71c4-4aab-8257-1625c6546ed7 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7e22f10f-71c4-4aab-8257-1625c6546ed7 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		First HD
root		(hd0,0)
chainloader	+1

title		Second HD
root		(hd1,0)
chainloader	+1


### END DEBIAN AUTOMAGIC KERNELS LIST

---

