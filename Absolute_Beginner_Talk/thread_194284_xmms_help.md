---
title: "xmms help"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by cac007 on 2006-06-11
Here is what it says when i ./configure

checking for GLIB - version >= 1.2.2... no
*** Could not run GLIB test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding GLIB or finding the wrong
*** version of GLIB. If it is not finding GLIB, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
***
*** If you have a RedHat 5.0 system, you should remove the GTK package that
*** came with the system with the command
***
***    rpm --erase --nodeps gtk gtk-devel
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

so i download and install glib 1.2 and come back to the xmms and it says the same thing?

---

### Post by asimon on 2006-06-11
If you want to compile xmms youself (xmms is already packaged for Ubuntu and in the main repository), you also need the -dev package for glib 1.2 and gtk+ 1.2, which include the respective header files. Thus you need to install
```

apt-get install libglib1.2-dev libgtk1.2-dev

```
too. Probably you need some more packages for xmms like for example libogg-dev and libvorbis-dev for ogg/vorbis support, etc. To make it easy you could just install
```

apt-get build-dep xmms

```
to install all the build dependencies of xmms.

---

### Post by cac007 on 2006-06-11
I just tried that and it is still showing the same thing :(

---

