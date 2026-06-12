---
title: "Feisty Boot up"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by abijah on 2007-05-20
How do i see the boot up process screen at start-up and not the image?

---

### Post by Iarwain ben-adar on 2007-05-20
Remove the 'splash' option in grub


Iarwain

---

### Post by abhishek456 on 2007-05-20
open grub menu.lst by typing > gksu gksu gedit /boot/grub/menu.lst

now go to the line starting with Kernel> kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=........................... ro quiet splash. At the end of the same line you will find quiet splash.

Remove splash save the file and that's it

---

### Post by Klargodut on 2007-05-20
and also remove quiet if you want to see more than what's printed by default.

---

### Post by abijah on 2007-05-20
Thanks!

---

