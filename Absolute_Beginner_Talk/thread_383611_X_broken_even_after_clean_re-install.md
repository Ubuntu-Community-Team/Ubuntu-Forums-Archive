---
title: "X broken even after clean re-install"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Ron.Mower on 2007-03-13
Hello,

A few weeks ago I installed Edgy into an AMD-32 machine with a Matrox G550 graphics card and 2-monitors (GRUB dual boot with Win XP).  Piece of cake!  Everything worked fine (except the second monitor ... but not big worry now)

[off topic] Later, after installing KDE, the computer would not completely power down anymore, it would just suspend to RAM.    

One day I was fooling around with WINE and the system froze solid.  After I restarted with a hardware reset,  Ubuntu would not start X (after selecting the GRUB boot option).  After a few seconds of blank screen, the system and monitor went to sleep.  No problems getting into a command line boot.

After some frustration, I decided to just start from a clean slate and I reinstalled Edgy onto a freshly formatted partition.  But!  I have the same problem!   X will not start.

Xorg.conf shown the Matrox card with an "mda" driver (changing "mda" to "vga" did not work)

Does anyone have a clue why Edgy would install once, but not twice?

Suggestions most welcomed!

---

### Post by Kobalt on 2007-03-13
Your problem is kind of weird Ron.Mower... Does a LiveCD session starts at least ?

---

### Post by dannyboy79 on 2007-03-13
try vesa instead of vga. I think vesa is the driver most compatible with every vid card. also, once you log into your ubuntu thru a cli, can you just do sudo dpkg-reconfigure xserver-xorg

---

