---
title: "Grub Menu.lst help please!!"
date: 2012-03-22
forum: Any Other OS
---

### Post by Jarkovskii on 2012-03-22
I am trying to create a menu.lst to be able to boot BackBox off a USB
 
I will also be adding OS choices once this is working.
 
I have my memory pen with:
 
G:> ls
 
menu.lst glrdr *BackBox*
 
G:/BackBox (this has everything thats extracted from BackBox.iso)
 
My menu.lst looks like this
 
splashimage /jozette.xpm.gz
color black/red yellow/green
timeout 120
 
title BackBox
root (hd0,0)
kernel /BackBox/casper/vmlinuz root=/dev/sdb1 ro quiet splash
initrd /BackBox/casper/initrd.gz
boot
 
 
It starts booting BackBox and shows the BackBox Linux: Penetration Testing Distrobution splash screen, but then stops the booting process and says: 
 
No init found. Try Passing init= bootarg.
 
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs)
 
 
 
Anybody have any ideas?

---

### Post by oldfred on 2012-03-22
Welcome to the forums.

Moved to otherOS.

I would think the root should be (hd1,0) if using sdb?

---

