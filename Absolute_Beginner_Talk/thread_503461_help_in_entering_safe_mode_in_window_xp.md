---
title: "help in entering safe mode in window xp"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-17
how do i enter window xp safe mode i dual boot ubuntu and window xp now i don't know how to boot into safe mode

---

### Post by pyros on 2007-07-17
> **zerobinary said:**
> how do i enter window xp safe mode i dual boot ubuntu and window xp now i don't know how to boot into safe mode

try hitting f8 right after grub starts to load xp. If you can't get that working, try powering off the machine while the windows splash screen is up, that should give you the option of starting in safemode the next time you boot.

If you can get into windows, just run msconfig, then look under the boot.ini options for the safeboot option.

---

### Post by zerobinary on 2007-07-17
but if i use safe mode will i be able to use bitcomet in there

---

### Post by pyros on 2007-07-17
> **zerobinary said:**
> but if i use safe mode will i be able to use bitcomet in there

weeelllll... no clue. regular safe mode doesn't have networking support, but there is an option on the menu you see when windows restarts after a failed boot that has an option for networking support.

---

### Post by raywood on 2007-07-18
I've had a similar problem.  Getting into safe mode sometimes takes a couple of tries.  It seems to help if I start punching F8 before the Grub screen even comes up, and continue instantly after choosing Windows.

---

### Post by Golyadkin on 2007-07-18
In safe mode you run a different user account, and many programs won't work that way because many services will be disabled. If you chose Safe mode with Networking, it is possible bitcomet might work, but why would you want to do that? Safe mode is only for emergency repairs, just boot into XP regularly (or Ubuntu) to run programs and download things.

---

