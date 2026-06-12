---
title: "Edit menu.lst in Knoppix?"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by siorai on 2005-12-22
I'm in the middle of removing my Windows drive entirely. I have reinstalled GRUB onto my Ubuntu drive (had two harddrives in system, now only one), but I have hit a problem. I need to edit my menu.lst so the hd entries are correct, but I can't figure out how to do it in Knoppix. Is it possible to do within Knoppix and if not, how would I go about editting it?

Edit:  Nevermind. With a bit of searching, I found out about how to edit the GRUB lines when you're in GRUB itself. :)

---

### Post by localzuk on 2005-12-22
Just so others know if they find this post in the future. The way to do it is to select the entry in the Grub menu and press e. Select the line you wish to enter and press e again. Alter what you want and press enter. Now press b to boot to that entry. Do this on only the option you wish to boot into as the changes are reverted each boot.

Now you can alter /boot/grub/menu.lst from the normal ubuntu environment.

---

