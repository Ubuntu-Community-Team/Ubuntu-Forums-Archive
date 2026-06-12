---
title: "[SOLVED] Can't put My Home on the Desktop"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-11-10
Hi, Just installed a fresh install of Ununtu 7.10.
Before I could just drag my Home folder from the Places
Bar to my Desktop and it would make a shortcut for me.

Well this time when I installed, I created a separate
Home Partition. My home is still in the Places panel
but now I can't drag it to my Desktop.... Is this
because I made a separate partition for it or is
something different in 7.10?

---

### Post by Perpetual on 2007-11-10
alt+f2, type gconf-editor apps>nautilus>desktop and enable the items you want.  I also use a seperate /home partition and when I try to drag and drop get an error 'You cannot move a folder into itself'.

---

### Post by Tyke91 on 2007-11-10
The desktop folder is inside the home folder   (your desktop is actually called /home/YourUserName/Desktop). dragging it inside itself would cause an infinite loop of files - generally a bad thing.


I'm curious as to how you did it in the first place...


EDIT: wow :) ninja posted.

anyway, that's really cool how you can make a home icon ( i never knew that before)

i guess it bypasses that infinite loop by making a separate Desktop folder that has all the links copied to it, except the home file?

---

### Post by init1 on 2007-11-10
> **Orbital75 said:**
> Hi, Just installed a fresh install of Ununtu 7.10.
Before I could just drag my Home folder from the Places
Bar to my Desktop and it would make a shortcut for me.

Well this time when I installed, I created a separate
Home Partition. My home is still in the Places panel
but now I can't drag it to my Desktop.... Is this
because I made a separate partition for it or is
something different in 7.10?
This is probably just a change in Nautilus. Do a
```

ln -s ~ ~/Desktop

```
in the terminal to make the shortcut.

---

### Post by Orbital75 on 2007-11-10
Thanks for the speedy response guys....
Yeah before In 7.04, I just dragged it out
of the Places menu onto the desktop and it
worked like a charm......

---

### Post by meindian523 on 2007-11-11
> **Perpetual said:**
> alt+f2, type gconf-editor apps>nautilus>desktop and enable the items you want.  I also use a seperate /home partition and when I try to drag and drop get an error 'You cannot move a folder into itself'.

+1,that's the proper way to get the stuff you want on the desktop.......

---

