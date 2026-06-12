---
title: "Problem with GTK graphics"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by rajaram_s on 2008-03-27
Hey... am using compiz on ubuntu 7.10. As soon as I enable desktop effects, any single desktop effect for that matter, my window border disappears. If i set the the "none" for desktop effects, I get a proper window border etc., What do I do? the issue is this happened suddenly.... for many days, I was using these desktop effects without any problem.

---

### Post by Therion on 2008-03-27
That's Emerald messing with you.  Try this:```
emerald --replace
```And see if that straightens things out.  Conversely, try opening CCSM (click on Advanced Desktop Settings in the System Preferences menu) and see if you have the Windows Decorations plugin enabled.  Sometimes switching this setting around can get things ironed out.

---

### Post by ahsile on 2008-03-27
This most likely means that compiz is failing, and then not putting metacity back in place afterwards. First, to fix the border issue:

```
metacity --replace
```

Second, you may want to start compiz from the command line and see if it prints any strange error messages before exiting.

Have you changed anything recently which may have lead to these problems?

---

### Post by rajaram_s on 2008-03-29
ya.. thank you... my resinatllation of compiz worked....

---

