---
title: "OpenGL Hardware-Rendering PowerBook G4?"
date: 2016-02-14
forum: Apple Hardware Users
---

### Post by kate-libby on 2016-02-14
How can i activate hardware-rendering on opengl? i have a pb 5,8 15" with ATI 9700 128mb. The OS ist Ubuntu 12.04 with latest Kernel 3.2.98.

---

### Post by gbjiulian on 2016-02-14
Try Ubuntu 15 its the latest software from Canonical

---

### Post by kate-libby on 2016-02-14
All Verions after 12.xx not work (graphics green inverted, freezes etc)...

---

### Post by lowtech2 on 2016-02-15
There is still a bug in Mesa up to recent version 11.1.1, which is used in Ubuntu 16.04 alpha2.
[https://bugs.freedesktop.org/show_bug.cgi?id=71789](https://bugs.freedesktop.org/show_bug.cgi?id=71789)

For a workaround, look at this web site and search for r300:  
[https://wiki.debian.org/PowerPC/FAQ#How_do_I_get_graphics_working.3F](https://wiki.debian.org/PowerPC/FAQ#How_do_I_get_graphics_working.3F)

---

