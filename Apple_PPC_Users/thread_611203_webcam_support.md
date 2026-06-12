---
title: "webcam support"
date: 2007-11-12
forum: Apple PPC Users
---

### Post by fuoco on 2007-11-12
There seems to be a driver called GSPCA which supports lots of webcams. This seems to be available under i386 and other archs but for some odd reason not in powerpc - any idea why that is so, and how to get it?

---

### Post by stmiller on 2007-11-14
Just searching google it seems that that particular driver is platform independent. So should work fine. However Ubuntu doesn't seem to include a package for it, so you would have to compile the driver. :(

[http://packages.ubuntu.com/gutsy/graphics/gspca-source](http://packages.ubuntu.com/gutsy/graphics/gspca-source)

Lots of newer video capture drivers are somewhat bleeding edge and are slow to be added to the Linux kernel, unfortunately.

---

