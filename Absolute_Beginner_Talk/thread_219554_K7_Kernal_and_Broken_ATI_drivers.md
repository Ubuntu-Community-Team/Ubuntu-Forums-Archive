---
title: "K7 Kernal and Broken ATI drivers"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by white on 2006-07-20
I recently updated from the 386 to the k7 kernal using this [**guide**](http://ubuntuforums.org/showthread.php?t=85917) and everything booted fine. No X problem at all, but then I checked to see if it broke my graphics driver and it put me back to the Mesa3d problem.

```
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

Do I completely reinstall the drivers or do I need some restricted modules I might be missing?

The guide said updating your kernal could break nVidia drivers but was really vague on other drivers.

My hardware is in my sig. :-D

---

### Post by FuzZy2006 on 2006-07-20
Loooooool everybody uses the term kernel. What's that a Kernal?

---

### Post by white on 2006-07-20
Ok, I've managed to fix it. I had to recompile the kernel module.

D'oh!

And as for the spelling I guess I'm used to spelling it that way. Oh well, at least the message gets across. lol

---

### Post by mcduck on 2006-07-20
> **FuzZy2006 said:**
> Loooooool everybody uses the term kernel. What's that a Kernal?

Kernel is the core of operating system. It's the part that actually makes your computer work, handling all installed devicec etc.

---

