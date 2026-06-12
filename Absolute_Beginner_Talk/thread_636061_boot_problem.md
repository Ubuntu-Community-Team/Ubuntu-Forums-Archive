---
title: "boot problem"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by kfir on 2007-12-09
hello!
after grub loading i get this eror:
> check root=booting cat /proc/cmdline
or missing ,modules , devices:cat/proc modules ls/dev
alert! /dev/disk/by-uunid/7a29fc95-5fbb-4860-9167-cbc60cb4d2d2 does not exits/
dropping to a shell!
busy box v1.1.3 (debian 1:1.1.3-5ubuntu7 built in shell (ash
enter help for a list of built-in commands
(initramfs
what does it mean and what to do???
thanks

---

### Post by kfir on 2007-12-09
??
please!!!

---

### Post by mhl978 on 2007-12-14
Figure out which partition you should be loading from (be sure you have the correct one) using the Partition Editor on the LiveCD.  Reboot and when you get to the grub menu, press 'e' to edit your ubuntu startup item.  Here, choose the line that includes 'root=' and change it to 'root=/dev/[NAME, ex. sda1]'.  Then go ahead and hit 'b' to boot.  Any changes made here will not be saved, but will be used temporarily - only for that boot.  If that is successful, you can change the assignment permanently by running 'sudo gedit /boot/grub/menu.lst' from terminal and editing it again.  Best of luck!

---

