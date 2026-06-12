---
title: "installing atk-1.9.1"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by samoht_okpoh on 2008-04-15
So, I ran ./configure and got this error:

> checking for GLIB - version >= 2.5.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.14.6, but GLIB (2.14.1)
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

I found this advice on the forums, but had no idea how to use it. 

> You have to modify your /etc/ld.so.conf file.

su - (or use sudo)

vi /etc/ld.so.conf

Add the an entry of the path you installed glib. For example, on my machine, downloaded the tarball to my desktop and copied it over to /usr/local/src. From there, I unpacked the tarbal and installed glib. So, my entry in ld.so.conf looks like this...

/usr/local/src

Once you make the modification, just type ldconfig from the command like to export your new change.

Kew? Iorked fine for me after that modification. If for some reason you forgot where you installed it, just do a search for the term glib...

find / -name glib

So, could someone explain?

---

### Post by Air_Scythe on 2008-04-16
First go into system/administration/synaptic package manager

then go into settings/repositories

click on updates and under ubuntu updates tick everything but pre released updates

now u should be able to find the new version by searching semantic, but i think ubuntu already comes with glib so run the update manager first.

---

