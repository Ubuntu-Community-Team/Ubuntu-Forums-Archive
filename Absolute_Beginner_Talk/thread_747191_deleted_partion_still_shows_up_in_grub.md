---
title: "deleted partion still shows up in grub"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by bovus on 2008-04-06
Recently, I have deleted a partition of ubuntu using gparted and installed ubuntu again on another partition.  However, the old patition still shows up in grub when it asks which OS i want to use.  If I select the deleted partition it just says that it does not exist.  Any way to remove the old partition as an OS to select in grub?  thanks

---

### Post by Martje_001 on 2008-04-06
Yes, you have to edit your */boot/grub/menu.lst*. If you don't understand the file, please post the file here, so I can help you.

---

### Post by bovus on 2008-04-06
I got it, thanks! The menu.lst file was pretty self explainitory.  Now that ive found that file, is there a way to boot a specific OS with having to choose one?

---

### Post by autocrosser on 2008-04-06
The first OS in menu.lst is the default boot

---

### Post by Duck2006 on 2008-04-06
> **bovus said:**
> I got it, thanks! The menu.lst file was pretty self explainitory.  Now that ive found that file, is there a way to boot a specific OS with having to choose one?

change the line

default         0

To what ever OP you want to boot by default,
If i want to boot the second OS then count down to the OS's and the number you get change the default line to match.
ie This is my menu.lst and if i want win to boot first then i would change the default to 3 
> 
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b78d5ed8-da06-468b-aa1a-6761eba0241e ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b78d5ed8-da06-468b-aa1a-6761eba0241e ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title          Windows NT/2000/XP
root           (hd0,0)
savedefault
chainloader    +1

---

### Post by Martje_001 on 2008-04-06
> **Duck2006 said:**
> ie This is my menu.lst and if i want win to boot first then i would change the default to 3
So start counting with zero!

---

