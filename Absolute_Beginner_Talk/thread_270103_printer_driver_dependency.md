---
title: "printer driver dependency"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-02
any idea what package is needed for this to install correctly?

```
In file included from rastertospl2.cpp:22:
../include/raster.h:25:25: error: cups/raster.h: No such file or directory
../include/raster.h:38: error: ISO C++ forbids declaration of ‘cups_raster_t’ with no type
../include/raster.h:38: error: expected ‘;’ before ‘*’ token
../include/raster.h:39: error: ‘cups_page_header_t’ does not name a type
make[1]: *** [rastertospl2.o] Error 1
```

---

### Post by shanepardue on 2006-10-02
i have a feeling the splix driver is too complex for me as it requires changing the source file by way of subversion. anyone ever do this?

---

### Post by scrattox on 2006-10-02
Well, the two development libraries for cups are:
[LIST]
[*]libcupsimage2-dev
[*]libcupsys2-dev
[/LIST]

So I would guess it would be one or both of those.

I found this information with:
```
apt-cache search --names-only cups | grep dev
```
from the command line.

(If you don't know what these commands do, you may find the commands "man apt-cache" and/or "man grep" useful.)

Good luck! :)

---

