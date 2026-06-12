---
title: "How do I install this splash screen?"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-10-14
I don't know how to install it, I tried the splash manager thingy and that didnt work, then I looked at the read me, tried that and it didnt work either. What do I do?

---

### Post by aysiu on 2006-10-14
Are you talking about a bootsplash, a usplash, or a login splash? Are you using KDE, Gnome, or XFCE?

---

### Post by moffa on 2006-10-14
Rename the file to splash.xpm.gz
Move it to the /boot/grub/ folder
Run the command "sudo update-grub"

If it doesn't work that means that the resolution may be incorrect.

---

