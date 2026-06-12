---
title: "Installing gtk+"
date: 2010-01-18
forum: Art &amp; Design
---

### Post by piperdown10 on 2010-01-18
I'm trying to install gtk+ and realized that I need to install glib, Pango, atk and cairo. I've installed glib-2.22.4 and Pango 1.26.2 but while installing atk-1.28.0, I received the following error:

```
checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.22.4, but GLIB (2.22.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.0.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/. If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
```

I'm not sure where to go from here. I tried looking for GLIB 2.22.3 and couldn't find it. Any help would be appreciated.

Thanks!

---

### Post by piperdown10 on 2010-01-18
Also, I've just installed cairo through apt-get.

---

