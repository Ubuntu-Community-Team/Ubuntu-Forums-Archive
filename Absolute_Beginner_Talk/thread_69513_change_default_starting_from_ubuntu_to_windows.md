---
title: "change default starting from ubuntu to windows"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by azuna on 2005-09-27
how to configurate ubuntu as webserver?

---

### Post by xmastree on 2005-09-27
[QUOTE=azuna]i want to change first select OS menu[/QUOTE]
```
sudo  gedit /boot/grub/menu.lst
```And change the default option. The comments in the file explain all.

---

### Post by davmac on 2005-09-27
You need to edit grub's menu list. It might be a good idea to take a backup first though with "sudo cp /boot/grub/menu.lst /boot/grub/menu.backup". Just in case it gets messed up it's also worth making sure you have a live CD to hand, so you can get back in and fix anything.

To edit the menu, open up a terminal and type "sudo gedit /boot/grub/menu.lst".

You'll see near the top of this file a line that says something like "default 0" (I'm on a Win2k box at work so can't check the exact format). You can change this value to where ever Windows sits in the order.

For a "standard" install you'll have Ubuntu at position 0, Ubuntu recovery at posn 1, memtest at posn 2, the divider bar at posn 3 (yes, this is counted) and Windows at posn 4.

The other alternative is to select/cut and paste the windows section to just above Ubuntu, putting it at posn 0 in the list.

HTH,

Dave Mac

---

