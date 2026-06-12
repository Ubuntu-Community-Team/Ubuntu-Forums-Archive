---
title: "modifying files as root"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by jiyongjiyong on 2007-07-20
being a kubuntu user precedently, i'm not finding out how to modify files as root.  in kubuntu, i just had to make a right click, and go in action->edit file as root, but apparently they don't have it in ubuntu-gnome. do i have to pass by the console to modify root files? thank you(the answer will be enough with a yes or a no!)

---

### Post by MohitRajani on 2007-07-20
yes. you need to use the console and can use the sudo command to modify root files.

---

### Post by AlexenderReez on 2007-07-20
you can modify using terminal
to edit file like use

> gksudo gedit <filename>

same as to run root application from terminal...

> gksudo <application>

or to modify anything in root partition use

> gksudo nautilus

---

### Post by xpod on 2007-07-20
> do i have to pass by the console to modify root files? thank you(the answer will be enough with a yes or a no!)

No

alt-f2 and type in.....
```
gksudo gedit path/to/file.name
```

or you could always use the terminal:)

---

