---
title: "My ubuntu can not begin...Emergency!"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2008-03-20
i have a laptop which has the ati radeon x1600 vga card ,tried to enabled via the restricted device manager and after logging out a "new" operational system appeared I think that that was Xubuntu (this iso cd comes from the linuxformat Greece magazine).Then restarted the computer and after that Ubuntu never has  loaded  yet....it  "jams" in with a black screen and seconds after , the hard drive stops reading or writing...This must be very serious!

Please help me with this.

---

### Post by Victormd on 2008-03-20
Have you tried loading in safemode?

When the Grub menu comes up, select the first option and type "e". This will allow you to edit that line.  At the end of the line, add the term "noapic" without "" and see if that helps.

---

### Post by chips24 on 2008-03-20
what version of ubuntu?

---

### Post by chemicalgr on 2008-03-20
It's the gutsy edition and noapic didn't help ...noapic with space after the end or without?

---

### Post by Victormd on 2008-03-20
With space. Should look something like this:

> kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0ed15c38-e72c-4182-9428-3ab9597ff5f9 ro quiet splash noapic --

---

