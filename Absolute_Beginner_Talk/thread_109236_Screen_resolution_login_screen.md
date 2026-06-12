---
title: "Screen resolution login screen"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by Deneb Algedi on 2005-12-28
My login screen(where you enter name+password) has a resolution of 1280X1024. How can I change it to 1024X768?
Just to be clear: I am not talking about my personal desktop resolution.

---

### Post by shin on 2005-12-28
Try following the guide: 
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Probably you're missing some modeline.

---

### Post by aysiu on 2005-12-28
Or ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Tack on vga=791 to the kernel line. For example, if your relevant entry looks like this ```
title Ubuntu, kernel 2.6.10-5-386
root (hd0,6)
kernel /vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash
initrd /initrd.img-2.6.10-5-386
savedefault
boot
``` Change it to ```
title Ubuntu, kernel 2.6.10-5-386
root (hd0,6)
kernel /vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash **vga=791**
initrd /initrd.img-2.6.10-5-386
savedefault
boot
``` Save (control-x), confirm (y), and exit (Enter).

---

