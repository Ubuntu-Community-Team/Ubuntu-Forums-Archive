---
title: "Deleting old kernel Ubuntu from GRUB help"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Clark Nova on 2006-10-08
I want to edit my GRUB loader so that it doesn't contain all of the old references before I updated to Edgy. This is my **/boot/grub/menu.lst**:

> 
title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=95055f2c-4bd6-43f6-81d3-78579c17a6d2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1



Can I safely delete all of the sections that make reference to kernel verion **2.6.15-27-386**?

---

### Post by catlett on 2006-10-08
Yes
```
gksudo gedit /boot/grub/menu.lst
``` Then delete the entries or put a # in front of them if you want to keep them for backup but you don't want to see them in the menu.
You can also delete the kernels themselves and not just the grub entry. Either use synaptic package manager or do it with nautilus by browsing as root to /boot and deleting the .15 versions ```
gksudo nautilus
```

---

### Post by h2gofast on 2006-10-08
if you uninstall them using synaptic, they should be automtically removed from the grub menu.  You can always reinstall them.

---

