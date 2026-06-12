---
title: "installing gtk / glib"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by MajesticHazard on 2007-08-03
I'm trying to install an application called Scatterchat ([http://www.scatterchat.com/download.html](http://www.scatterchat.com/download.html)). I got as far as compiling and installing all of the necessary parts, but when I configure the last bit of source I get this error:

checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.6.6, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at [http://www.gtk.org/](http://www.gtk.org/).

So I went to that URL and got myself the latest version of GLib. I tried again and got the same error. I decided that the problem might be that I don't have the right version of gtk+, but I could find out by trying to configure the source - if it's not there already then its dependencies won't be there either, so it won't work. It didn't. I then downloaded those dependencies, but I had a problem configuring atk-1.9.1. I got this error:

checking for GLIB - version >= 2.5.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.6.6, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

I'm not sure how to do that, though, if that is in fact the problem.

---

### Post by asmoore82 on 2007-08-04
do you really need this scatterchat ...
it is self-admittedly based on Gaim which is now obsolete and unsupported code
~ [http://gaim.sourceforge.net/](http://gaim.sourceforge.net/) ~ and witness the re-direct.

---

