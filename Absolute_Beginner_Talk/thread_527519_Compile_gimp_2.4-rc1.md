---
title: "Compile gimp 2.4-rc1"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by tones111 on 2007-08-16
I've been anxiously awaiting (for some time, just like everyone else) for Gimp 2.4 to arrive and noticed the first release candidate came out today.  I'm attempting to compile it and running into difficulties.

the configure script is looking for GTK+ >= 2.10.13 but Feisty is only running with 2.10.11-0ubuntu3.  So, I downloaded the latest version (2.10.14) from [ftp://ftp.gimp.org/pub/gtk/](ftp://ftp.gimp.org/pub/gtk/), and the install went without any problems.  However, now the gimp configure script is complaining that...

*** 'pkg-config --modversion gtk+-2.0' returned 2.10.14, but GTK+ (2.10.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GTK+. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

which makes sense because removing the original GTK with Synaptic would have uninstalled anything related to GTK.  So, how do I go about switching my environment to the newly installed version and removing the old version?  Thanks for any help.

---

### Post by bogolisk on 2007-08-16
I stumbled upon [http://buzz.ulx.ru/gimp.html](http://buzz.ulx.ru/gimp.html), it might or might not help!!!

---

### Post by tones111 on 2007-08-17
Thanks for the link.  I also ran across a deb package for rc1 at [http://ubuntuforums.org/showthread.php?t=311020&page=10&highlight=gimp]("http://ubuntuforums.org/showthread.php?t=311020&page=10&highlight=gimp")

The package installer said all dependencies were satisfied but when installing it says "failed to install package 'gimp-2.4.0_rc1-1_i386.deb'".  The terminal output seems to be stuck at "(Reading database ... "

I wouldn't mind running a pre-built executable if it would install but would still like to know how to go about updating the GTK libraries when newer versions are released.  How painful is the process?

---

### Post by rev_b on 2007-08-17
I'm also experiencing troubles compiling gimp 2.4. I keep getting the error "checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.12.3... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: Test for GLIB failed. See the file 'INSTALL' for help."

I compiled and installed glib-2.14-0, but it still can't find it.

The deb also won't install, I get "dpkg: error processing gimp-2.4.0_rc1-1_i386.deb (--install):
 trying to overwrite `/usr/bin/strip', which is also in package binutils
dpkg-deb: subprocess paste killed by signal (Broken pipe)"

---

### Post by tones111 on 2007-08-17
I got the same thing (or very similar) when compiling also.  Installing the libglib2.0-dev package should fix that problem.

---

