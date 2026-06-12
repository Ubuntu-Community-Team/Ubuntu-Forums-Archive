---
title: "[SOLVED] Pismo External Display Mirroring"
date: 2008-08-20
forum: Apple Hardware Users
---

### Post by gaussian on 2008-08-20
I just installed Gutsy (actually installed Feisty and upgraded to Gutsy) on my Pismo (G3 laptop). I would like to use an external display (data projector) mirroring the main screen. Can this be done under any Ubuntu version? Googling provides links to m3mirror, but if I understand correctly, it does not support Pismo and requires custom Kernel. Has anyone done this?

---

### Post by DGortze380 on 2008-08-20
> **gaussian said:**
> I just installed Gutsy (actually installed Feisty and upgraded to Gutsy) on my Pismo (G3 laptop). I would like to use an external display (data projector) mirroring the main screen. Can this be done under any Ubuntu version? Googling provides links to m3mirror, but if I understand correctly, it does not support Pismo and requires custom Kernel. Has anyone done this?

You should be able to clone your output with the default display options in ubuntu.

---

### Post by gaussian on 2008-08-21
> **DGortze380 said:**
> You should be able to clone your output with the default display options in ubuntu.

Thank you for the suggestion. Unfortunately, the standard display tools in (gtk-displayconfig) Ubuntu did not do the trick. However, adding:

```
 Option "Display" "Mirror"
```

In xorg.conf did the trick. For future reference see: 
```
man r128
```
This will Mirror X output, but not virtual terminals, but that is ok for my purposes.

---

