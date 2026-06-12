---
title: "Dual boot windows first"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Eldar11 on 2007-08-06
how would I be able to change the boot settings to make the computer boot into Windows as the default not Ubuntu?

---

### Post by overdrank on 2007-08-06
> **Eldar11 said:**
> how would I be able to change the boot settings to make the computer boot into Windows as the default not Ubuntu?

Hi you can do this by editing you grub
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
Good luck! And Be careful! :popcorn:

---

### Post by Rocket2DMn on 2007-08-06
You can try opening your menu.lst file and moving the entry for Windows above the other entries
Let's make a backup first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
Ah, and here is a good example: [http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)  - It says to change "default" from 0 to 1 as well.
Good luck.

---

### Post by bruckwine on 2007-08-06
Yes I changed the default to 5 rathe than move the Windows load entry in GRUB and it works fine - doesn't look as nice with the bar starting at the bottom, but functional!

---

