---
title: "glib pkg-config error"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by MajesticHazard on 2007-08-05
On ./configure'ing the source code for a program I dled, I get the following error message:

```
checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.8.6, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
```
```

pkg-config --modversion glib-2.0
``` returns 2.8.6 as I recently installed the latest version of glib.
I don't know where to begin following the instructions in the error, though. Can someone walk me through it?

---

