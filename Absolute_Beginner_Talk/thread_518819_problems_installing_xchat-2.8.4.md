---
title: "problems installing xchat-2.8.4"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mandarke on 2007-08-06
i'm getting this error when i try to install the latest xchat (2.8.4):

checking for GLIB - version >= 2.0.3... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: "Cannot find glib"

i've looked in synaptic for the glib package, but all i can find is documentation for it. what am i doing wrong?

---

### Post by nichipet on 2007-08-06
I believe xchat is available through apt-get/aptitude. Assuming you are doing a custom compile, have you tried installing glib through apt-get/aptitude? A quick search of Google showed it should be available there. Of course, use apt-cache search glib first to find the exact name of the package.

---

### Post by mandarke on 2007-08-07
the version of xchat on apt is very old.

i've managed to solve this problem after looking at the fedora rpm version :\

---

