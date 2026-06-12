---
title: "program (XMMS and MC) can't be compiled manually.. glib is not found"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by mushu on 2005-06-26
i have some problems.. i'm new to linux and ubuntu.. since i don't have any internet connection at my dorm the only thing i can do to install program into my ubuntu box is by compiling itself using tar.gz files because i can't do the apt-get install command..

Now i want to installed xmms and mc (midnight commander) into my box and both files have tar.gz extension.. i've unpack them and do the ./configure.. but i can't finish the ./configure phase, i've received error message which tell me that i don't have glib installed.. this is what it said..

for xmms...
------------------
creating libtool
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***


and this is for mc
---------------------
checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
checking for glib-config... no
checking for glib12-config... no
checking for glib-config... no
checking for GLIB - version >= 1.2.6... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Test for glib failed.
GNU Midnight Commander requires glib 1.2.6 or above.

i've checked my synaptic package manager and there are libglib2.0.0 (if i'm not mistaken') installed.. so how can i install xmms and mc? by compiling itself? or are ther another way to do it? thanks.. :)  :)

---

### Post by az on 2005-06-26
Good question!

You need build-essential.  It is on your cd.  In will install the compiler and essential headers files.  If that is not enough to compile xmms, it is because you are missing other header files (libgtk1-dev, for example.)  For MC, I think you need libncurses5-dev.  Again, I do not know if it is on the cd.

What is on the cd is what you need to compile most extra modules needed for a net connection (modem driver, wireless driver)  The other -dev packages are only available in the online repositories...

You can download the mc binary package from universe, as will as xmms

packages.ubuntu.com

Save them and
cd (folder)
sudo dpkg -i (package.deb)

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=mushu]i have some problems.. i'm new to linux and ubuntu.. since i don't have any internet connection at my dorm the only thing i can do to install program into my ubuntu box is by compiling itself using tar.gz files because i can't do the apt-get install command..
[/QUOTE]

Where did you download the tar files? I would say you need to download the debs (and dependancy debs) for these files in the same place and install them.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

install the debs this way:

sudo dpkg -i debname.deb

Be sure to install the dependancies first. Thats still better than compiling from source....

---

### Post by mushu on 2005-06-27
okay.. so the conclusion is to use *.deb package rather than compiling the source file myself.. thanks for your help.. but i do have one more question, where can i get the mc with *.deb package? i can't find it on packages.ubuntu.com.. seems that i have to ask mr google again.. hehe :) thanx anyway..

---

