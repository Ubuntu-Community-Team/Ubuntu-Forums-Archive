---
title: "Graphics Drivers Specifiable in xorg.conf file"
date: 2007-06-29
forum: Apple PPC Users
---

### Post by flyinggeko on 2007-06-29
Can anyone give me a list of drivers that i can specify in the xorg.conf file found under /etc/X11?

---

### Post by pxwpxw on 2007-06-29
There may be a list, I dont know, but if you are lookig for a driver for your G4, it would be easier to find what graphic card you have, then take it from there
```

 lspci | grep VGA
 man ati radeon nv

```
 for a start.

---

### Post by stmiller on 2007-06-29
Choices for PPC Linux are:

Nvidia: nv

ATI: ati
radeon 
r128 (rage cards)

or generic display driver:

fbdev

---

