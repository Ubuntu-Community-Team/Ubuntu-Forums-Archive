---
title: "uninstall a program"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by XxBigP123xX on 2007-04-07
how do i uninstall a program in ubuntu and from wine?:confused:

---

### Post by alkat on 2007-04-07
> **XxBigP123xX said:**
> how do i uninstall a program in ubuntu and from wine?:confused:


Don't know about Wine, but for Ubuntu you can either use Synaptic, look for the program you want to uninstall and just select to remove it completely, or you can open a terminal and write the following:

$ sudo apt-get remove --purge program_to_uninstall

Ale.

EDIT: for Wine, check here:
[http://www.linuxforums.org/forum/wine/84648-uninstalling-windows-stuff-under-wine.html](http://www.linuxforums.org/forum/wine/84648-uninstalling-windows-stuff-under-wine.html)

---

### Post by celettu on 2007-04-09
For wine, open a terminal and type:

```
uninstaller
```

---

