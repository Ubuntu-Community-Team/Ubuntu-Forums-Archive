---
title: "Dual boot."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by kafro on 2007-08-18
After i install Ubuntu 7, my XP does not boot up ?.. 
What is the problem..?
It says "Starting up OS"
and just sits like that.

---

### Post by cbhargava on 2007-08-18
Does ubuntu start?

What was the sequence of OS installation?

---

### Post by jingo811 on 2007-08-18
Try Graphical GRUB editor if you can boot into Ubuntu.
[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

---

### Post by kafro on 2007-08-18
Ubuntu deos start, thats how i am typing right now.

---

### Post by cbhargava on 2007-08-19
looks like your bootloader is messed up. Check the grub config file (/boot/grub/menu.lst) and re-install the bootloder using grub-install.

---

### Post by kafro on 2007-08-19
> **cbhargava said:**
> looks like your bootloader is messed up. Check the grub config file (/boot/grub/menu.lst) and re-install the bootloder using grub-install.

Thats something i do not know how to do.

---

### Post by r4ik on 2007-08-19
Try,

[http://knowledge76.com/index.php/Restore_Grub](http://knowledge76.com/index.php/Restore_Grub)

Good luck !

---

### Post by kafro on 2007-08-19
Thanks ill will give it a try, and tell you what happens.

---

