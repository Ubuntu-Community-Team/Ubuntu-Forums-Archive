---
title: "configure GRUB"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by falkenberg_cph on 2006-06-14
Hi
Is it possible to make configuration to GRUB.
Optimal would be that i could have GRUB autostart linux without the "countdown screen", but still be able to enter XP very seldom (fx. via a key at the same time as you can enter BIOS and boot-device-screen).

Get it. i hope i explained it allright.
Carsten

---

### Post by Jeroen Vernooij on 2006-06-14
yes you can.
type ```
sudo gedit /boot/grub/menu.lst
``` in your terminal, and you can edit all of the entries, as well as the default delay.

---

### Post by Jeroen Vernooij on 2006-06-14
addition: in your case, I should uncomment (remove the # before it) hiddenmenu, so the menu won't show up if you don't press ESC, and set a time-out of 1 sec.

---

### Post by falkenberg_cph on 2006-06-14
Thanks alot

---

### Post by Jeroen Vernooij on 2006-06-14
Your welcome, good luck.

---

