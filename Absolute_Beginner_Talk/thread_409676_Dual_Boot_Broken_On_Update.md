---
title: "Dual Boot Broken On Update"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Razorback on 2007-04-14
I had a dual boot setup on 2 hard drives - one drive on IDE and one drive on SATA.  My IDE drive has Ubuntu and grub.  I had my menu.lst setup for XP to load but after an update the menu.lst did not show the XP boot text.  I know what needs to be setup but grub errors saying it cannot find the SATA.  Any help would be appreciated.  BTW Windows boots fine but I have to change the boot order in the BIOS - I just want to restore my old config. Thanks

---

### Post by BoneKracker on 2007-04-14
Could you post your /boot/grub/menu.lst file?

---

### Post by Razorback on 2007-04-14
> **BoneKracker said:**
> Could you post your /boot/grub/menu.lst file?


title		Ubuntu, kernel 2.6.15-28-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-28-686
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title		Microsoft Windows XP Home Edition
root		(hd1,1)
makeactive
savedefault
chainloader	+1

The last part is what I am trying to fix.  It was not there after the update.  I guess I need to back up the menu.lst file for the next update. ;)

---

### Post by confused57 on 2007-04-14
Try adding mapping lines:

title Microsoft Windows XP Home Edition
root (hd1,1)
makeactive
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by Razorback on 2007-04-14
Thanks a bunch - that was exactly what I was looking for. :)

---

