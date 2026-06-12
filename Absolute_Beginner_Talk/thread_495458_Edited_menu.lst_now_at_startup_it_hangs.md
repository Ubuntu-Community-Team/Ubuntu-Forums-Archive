---
title: "Edited menu.lst now at startup it hangs"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-08
in the menu.lst i added End Default options

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439f47e8> =vga=791initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

because I was getting a 20 second hang between startup and then login screen, now it shows everything booting up but at 6.616000 sr 1:0:0:0 Attached scsi generic sg5 type the comp hangs.

After a while it said /dev/disk/by-uuid/a86b2426-7c84-4b5e-8bca-4ff1439f47e8=vga=791 does not exist. Dropping to a shell!

BusyBox v1.1.1 (Debian 1:1.1.1-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin.sh: can't access tty; job control turned off
(initramfs)_

Is it possible to change my menu.lst somehow? What should I do?

---

### Post by ajmorris on 2007-07-08
> **snwbord2456 said:**
> in the menu.lst i added End Default options

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439f47e8initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

because I was getting a 20 second hang between startup and then login screen, now it shows everything booting up but at 6.616000 sr 1:0:0:0 Attached scsi generic sg5 type the comp hangs.

After a while it said /dev/disk/by-uuid/a86b2426-7c84-4b5e-8bca-4ff1439f47e8=vga=791 does not exist. Dropping to a shell!

BusyBox v1.1.1 (Debian 1:1.1.1-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin.sh: can't access tty; job control turned off
(initramfs)_

Is it possible to change my menu.lst somehow? What should I do?

from grub, use the recovery mode entry, that boots into a CLI, then remove the entry that mucked up the boot.

also add a space after the kernel part and add this : 
ro quiet splash vga=791

if you want vga=791


so that your entry looks like this :

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439f47e8 ro quiet splash vga=791
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

---

### Post by snwbord2456 on 2007-07-08
I'm the root now, but I don't know the syntax to change it, and I really dont want to do anything wrong because of the root. Where do I start?

---

### Post by ajmorris on 2007-07-08
> **snwbord2456 said:**
> I'm the root now, but I don't know the syntax to change it, and I really dont want to do anything wrong because of the root. Where do I start?

ah, now the tough part.... use vim :

type ```
vim /boot/grub/menu.lst
```


the insert key enables editing... then press Esc to stop editing after you have made the changes..... then when you are done editing and have pressed Esc, type ```
:wq
``` which is the VIM syntax to write the file then quit.

---

### Post by snwbord2456 on 2007-07-08
awesome, so now ubutnu loads, but I all the startup actions are displayed, is there any way to get rid of this?

---

### Post by ajmorris on 2007-07-08
> **snwbord2456 said:**
> awesome, so now ubutnu loads, but I all the startup actions are displayed, is there any way to get rid of this?

what do you mean by the startup actions are displayed?.... the splash screen?

---

### Post by snwbord2456 on 2007-07-08
I assume so, not so sure on the definition. Like:

*Loading Hardware drivers


and other things like that.

---

### Post by ~~Tito~~ on 2007-07-08
Yea I want that to go away to. Like after my computer manufacture's screen goes away and the grub thing goes away I want it to go straight to the Ubuntu title and the progress bar.

---

