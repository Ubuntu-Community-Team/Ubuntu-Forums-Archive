---
title: "Ubuntu 7.10: trouble building dependencies for freeciv-2.1.0"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by jrwh on 2007-11-21
I'm supposed to build five dependencies to install freeciv 2.1 for ubuntu 7.10.  I get to the third one, atk-1.8.0, and I end up with this message when I try to configure it:

checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.4.8, but GLIB (2.14.1)
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
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

Can anyone please help me with this problem?

---

