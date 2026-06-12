---
title: "One more package install question"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by mysticrider92 on 2006-08-31
I am installing the Anjuta IDE on my computer and it needs four packages: glib-2.0 or higher, gtk+-2.0 (I think), atk-1.0, and pango-1.0. I got glib-2.12.2 to install and now I need the others. When I try to run the "./configure" command for atk I get this error:
> checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.12.2, but GLIB (2.10.3)
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
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/).

I have already installed glib-2.12.2.I can't find the pkg-config file to edit it, and I can't find the old version of glib to remove it. Does anyone know where to look for these?

---

### Post by amo-ej1 on 2006-08-31
what's wrong with the anjuta package ?

---

### Post by mysticrider92 on 2006-08-31
Anjuta needs all of these packages, and I have to  install them through terminal using files on my desktop. I don't know the repository to tell the computer to look for them in.

---

### Post by mysticrider92 on 2006-08-31
I found a solution. I used the Automatix mentioned in a recent post.

---

