---
title: "Upgraded to glib-2.5 ...now a quandary"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by lazyart on 2006-10-18
Linux newb but adventurous...

Installed 6.06 a week ago, and I'm looking and learning.  Decided to install GNUCash.  1.8.x is available thru add/remove, but I wanted the latest stable 2.0.2.  So, I downloaded and tried to make.  Tells me I need glib 2.4 or greater.  Managed to make glib 2.5 (took a lot longer than this post might indicate).  So now I try to ./configure GNUCash and I get this message:


*** 'pkg-config --modversion glib-2.0' returned 2.5.0, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

*** GLIB >= 2.4 is required to build Gnucash; please make sure you have the
*** development headers installed. The latest version of GLIB is
*** always available at [ftp://ftp.gnome.org/pub/gnome/sources/glib/](ftp://ftp.gnome.org/pub/gnome/sources/glib/).


I'm terrified to remove glib 2.10.3 because when I try to, add/remove tells me that ubuntu desktop depends on it and will also be removed.

Any ideas on what I should do next?  Thanks.

---

### Post by jalirious on 2007-10-12
Yup. Sure izzz.....

Been scouring the net for ages now. Did you find a way?

---

### Post by lazyart on 2007-10-14
I'm running Feisty now and GNUCash runs like a champ.

---

