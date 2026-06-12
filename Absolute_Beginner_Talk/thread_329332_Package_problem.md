---
title: "Package problem"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by beamo on 2007-01-01
I'm trying to install xvidcap on an AMD 64 machine. I downloaded the .tar file, extracted it, and changed my directory to the extracted folder. When I run ./configure everything is good except for this error at the end:
> 
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 glib-2.0 gthread-2.0) were not met:

No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I've downloaded the libglade-2.0 .tar and gone through the same process with the same result - it needs another package. Is there any way to get all the stuff in one shot?

---

### Post by kepos on 2007-01-01
> checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.4.0 libglade-2.0 glib-2.0 gthread-2.0) were not met:

i'm not shure but try something like

```
sudo apt-get install libglade-2.0
sudo apt-get install glib-2.0
sudo apt-get install gthread-2.0
```

---

