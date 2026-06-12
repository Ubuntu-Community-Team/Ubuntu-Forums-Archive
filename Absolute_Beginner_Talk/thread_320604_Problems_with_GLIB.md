---
title: "Problems with GLIB"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by b0bby on 2006-12-17
Hey, Im trying to compile gimpshop, and it required a newer version of GLIB than i have currently.. So i compiled a newer version 2.6.6, but when running the ./configure for gimpshop it gives me this error;
```
checking for GLIB - version >= 2.4.5... 
*** 'pkg-config --modversion glib-2.0' returned 2.6.6, but GLIB (2.12.4)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: Test for GLIB failed. See the file 'INSTALL' for help.
```
And if I try to remove the GLIB installed from apt-get it want to remove a h*ll of alot more than just 'libglib2.0-0', like firefox, fluxbox, gaim, gftp etc.

How should I proceed? 
Everything went fine with the compiling of the newer GLIB, but 'pkg-config' still shows the old version :/

please help, Im new to compiling, but a 2-3 year full-time Linux-user.

---

### Post by arnieboy on 2006-12-19
instead of compiling from source, you can try the following and see if that works:
```
wget http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb
sudo dpkg -i gimpshop_2.2.11-1_i386.deb
```

---

