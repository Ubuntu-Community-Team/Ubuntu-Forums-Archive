---
title: "DOS text after last kernel update"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by pastalavista on 2008-04-20
After my last kernel update (2.6.24-16), on bootup, after the Ubuntu splash screen displays for a short time with an oscillating load bar, it then goes to a black screen that displays all the dos-like text of the boot process. It never did that with any previously installed kernels. How can I change it back to the way it was with only the boot process load bar graphic that actually showed the boot progress in the splash screen?

---

### Post by diablo75 on 2008-04-20
Well, the short term fix is to use grub to revert to the previous kernel.  The way I fixed this was to reinstall because I was lazy and expected problems since it's still beta software and expected problems.  But I do want to know the "proper" way to fix this kind of problem...

---

### Post by 1875 on 2008-04-20
Boot into previous kernel, apply any updates and try again.

---

### Post by pastalavista on 2008-04-22
I booted into older kernels and even tried recovery mode still the same thing. I looked at /boot/grub/menu.lst and it had "quiet" mode enabled which I thought was supposed to eliminate all that clunky looking text. Doesn't anybody know how to fix this? I looked at a program called "Startup Manager" but it warned not to use it with a dual boot setup (I dual boot WinVista). I hope this will get fixed with the final release version. And speaking of that, will I have to re-install from scratch? I had to start all over getting my system customized when I changed from Gutsy to Hardy beta... is there some way to upgrade to a new version and still keep my old version's settings and apps? (ie Compiz and Google Earth etc)

---

### Post by fidamehran on 2008-06-08
I need to know one more thing. Is there any such thing that, a Gnome update will come to cover the new kernel, so that the new updated kernel also shows GUI/desktop? It is really awkward to have the OS updated and not get a desktop for that...

---

