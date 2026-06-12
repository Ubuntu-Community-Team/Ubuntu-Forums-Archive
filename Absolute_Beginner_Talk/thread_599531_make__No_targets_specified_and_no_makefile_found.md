---
title: "make: *** No targets specified and no makefile found"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by ikak on 2007-11-01
Hi all,

I'm looking to install the program Gnome Outliner ([http://gnomeoutliner.sourceforge.net/](http://gnomeoutliner.sourceforge.net/)) and cannot find it in Synaptic.  So I've tried installing manually using:
Extracting the package.tar.gz
cd package
./configure
make
make install

but when I try 'make' I get an error saying:

make: *** No specified targets and no makefile found. Stop.

I've looked through other posts with the same error but nothing seems to help.  I have installed build-essential through apt-get and it still does not want to work.  Any ideas?

---

### Post by Maestro23 on 2007-11-01
> **ikak said:**
> Hi all,

I'm looking to install the program Gnome Outliner ([http://gnomeoutliner.sourceforge.net/](http://gnomeoutliner.sourceforge.net/)) and cannot find it in Synaptic.  So I've tried installing manually using:
Extracting the package.tar.gz
cd package
./configure
make
make install

but when I try 'make' I get an error saying:

make: *** No specified targets and no makefile found. Stop.

I've looked through other posts with the same error but nothing seems to help.  I have installed build-essential through apt-get and it still does not want to work.  Any ideas?

Are you getting any errors from the ./configure?  Any depdency issues (programs/files it needs)?

---

### Post by meatpan on 2007-11-01
Post the output you received when running './configure'

---

### Post by ikak on 2007-11-01
----------------------------------------------------------------------------------------------
checking for glib-2.0 >= 2.4.0 gtk+-2.0 >= 2.4.0 libxml-2.0 >= 2.6.8 libgnome-2.0 >= 2.6.0 libgnomeui-2.0 >= 2.6.0... Requested 'glib-2.0 >= 2.4.0' but version of GLib is 2.0.7 Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package libxml-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libxml-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libxml-2.0' found Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found
configure: error: Library requirements (glib-2.0 >= 2.4.0 gtk+-2.0 >= 2.4.0 libxml-2.0 >= 2.6.8 libgnome-2.0 >= 2.6.0 libgnomeui-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
----------------------------------------------------------------------------------------------

I'm assuming I need glib or gtk+ or one of the others and I tried doing the glib, gtk+ in the same was and got errors making that too.

----------------------------------------------------------------------------------------------
phill@ikak:~/Desktop/gtk+-2.10.9$ make
make: *** No targets specified and no makefile found.  Stop.
----------------------------------------------------------------------------------------------

---

### Post by Paul820 on 2007-11-01
You need all these:

> glib-2.0 >= 2.4.0
gtk+-2.0 >= 2.4.0
libxml-2.0 >= 2.6.8
libgnome-2.0 >= 2.6.0
libgnomeui-2.0 >= 2.6.0

It can't find any of them. Take note of the '>=' for the version number. All those packages should be available from synaptic.

EDIT: Make sure you get the dev packages, these are what are needed for compiling. So for example you should search for libglib2.0-dev for the first one.

---

### Post by Maestro23 on 2007-11-01
> **Paul820 said:**
> You need all these:



It can't find any of them. Take note of the '>=' for the version number. All those packages should be available from synaptic.

EDIT: Make sure you get the dev packages, these are what are needed for compiling. So for example you should search for libglib2.0-dev for the first one.

Paul820 beat me to the punch.:)

---

### Post by ikak on 2007-11-02
Thanks a lot guys! It worked... I've got the program installed.. my next question is, how do get an icon for said program in my Applications menu?

---

