---
title: "Installing Problems"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by SLEZ on 2007-11-04
I am new to ubuntu, just started using it yesterday. I have used redhat a while back, so I do understand the concept of what I am trying to do.

I am having a problem with install a program, I downloaded that tar file, extracted it to a folder in the desktop, i went to terminal and in the directory used the command ./configure

Everything goes fine till the last part

checking for GLIB - version >= 2.0.3... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: "Cannot find glib"

I then did,       sudo aptitude install glib
Seemed like it installed it but I still get the same error.

---

### Post by Maestro23 on 2007-11-04
You need libc6, maybe lib6c-dev.  Also if you are compiling something from source, make sure you have build-essential installed.

> sudo apt-get install build-essential

---

