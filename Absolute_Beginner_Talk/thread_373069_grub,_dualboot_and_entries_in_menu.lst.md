---
title: "grub, dualboot and entries in menu.lst"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by hamproof on 2007-02-28
Here's what is in my /boot/grub/menu.lst. Is it possible to remove kernel 2.6.17-10? How do I do it?

Thanks.


[I]title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1[/I]

---

### Post by dpar on 2007-02-28
You could just comment them out with # if you don't like seeing them in the bootloader. It's not really doing any harm being there.

---

### Post by hamproof on 2007-02-28
I am looking for a way to actually *uninstall* -10-generic.

I'm sure it's not as easy as deleting 1 or 2 files. I assume -10-generic probably installed a whole bunch of files specific to its release.

TIA

---

### Post by bodhi.zazen on 2007-02-28
> **hamproof said:**
> Here's what is in my /boot/grub/menu.lst. Is it possible to remove kernel 2.6.17-10? How do I do it?

Remove it via synaptic ....

---

