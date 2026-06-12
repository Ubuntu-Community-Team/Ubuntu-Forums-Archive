---
title: "Boot menu shows both 2.6.17-11 and 2.6.17-10"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by leftybob on 2007-02-10
The Grub menu is showing both 2.6.17-11 and 2.6.17-10 Ubuntu versions when I start my computer.   Everything seems to work when I choose the 11 version.  Is the 10 version something left over from an update?
Thanks in Advance

---

### Post by sardion on 2007-02-10
Yes, the -10 is left over from an update.

Most packages that get updated, the old version is removed.  But not kernels since they are too important for the system.

You can ignore it, but if it annoys you, you can remove the -10 version using synaptic or aptitude.

---

### Post by teaker1s on 2007-02-10
I leave an old kernel in grub just incase the new one borks my system, if you completely remove it from synaptic it will also update grub for you

---

### Post by nickoli_02 on 2007-02-10
You can also comment out the menu entry using

```
gksudo gedit /boot/grub/menu.lst
```

The menu entries are at the bottom :)

---

### Post by leftybob on 2007-02-10
Would you recommend keeping the 10 version in case there is a problem with the 11?
With both versions and their protected modes listed, the grub menu is a bit crowded, but if leaving the old one there is the wise thing to do I will.
Thanks

---

### Post by leftybob on 2007-02-10
Thanks folks - I replied before seeing the follow up answers.  Based on what you guys say, I think I will just leave it as is.
Thanks for helping a beginner...

---

### Post by teaker1s on 2007-02-10
a wise person:)

---

