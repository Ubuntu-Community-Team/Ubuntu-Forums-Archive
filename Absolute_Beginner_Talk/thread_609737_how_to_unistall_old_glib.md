---
title: "how to unistall old glib"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by rob1101 on 2007-11-11
well i am trying to install GTK 2.8 and i need to install its dependancies i installed glib but when i try to install atk i get this error.

```

checking for GLIB - version >= 2.5.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.8.6, but GLIB (2.14.1)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.8.6, but GLIB (2.14.1)
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

so my guess would be to uninstall the old glib but how do i do that exactly? and keep in mind that im a novice :P

---

### Post by pistcivet on 2007-11-11
What are you trying to build?

If you're building a package that says it requires foo-1.0
you will also need to install foo-1.0**-dev** (in a Debian-based distro like Ubuntu)

Kind of like Debian's version of dependency hell.
If this is old news to you, please disregard. :)

---

### Post by rob1101 on 2007-11-11
well im trying to install gtk2.8 right now and in order to install that it said i need  to install its dependencies which are:

glib
atk
pango
cairo 


i downloaded glib, unpacked it---> cd to the directory ---> ./configure ---> make ---> make install 

then when i try to do the same to atk i get the error when i do ./configure

i dont think it needs foo

---

### Post by pistcivet on 2007-11-11
To build from source, you need "this package"
Plus...
you need "this package"**-dev**

You need the "developer" or **-dev** version of all dependencies.
**in addition** to the plain old "non-dev" package for all dependencies.

What are you really trying to accomplish ? What is the final goal?
Because there is almost certainly an easier way.

---

### Post by rob1101 on 2007-11-11
trying to install [this]("http://murrine.netsons.org/") and i wanted to do it through the command line as a personal goal, for the learning experience. 

do you know where the old glib file would be? if i could find it couldn't i just compile that and run the unistaller

---

