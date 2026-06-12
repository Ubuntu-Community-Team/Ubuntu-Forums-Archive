---
title: "SICStus Prolog does not install correctly"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by cluelessCS on 2007-06-28
Hi

I am trying to install [Sicstus Prolog](http://www.sics.se/isl/sicstuswww/site/portability.html),
but there are some problems when I run the installation file:

> 
Checking installation cache... install.cache
dummy.c:1:19: error: stdio.h: No such file or directory
dummy.c:2:30: error: gnu/libc-version.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:1:19: error: stdio.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:2:22: error: features.h: No such file or directory
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c: In function ‘main’:
/tmp/tmp.AgLYgB8953/dummy_8948_20070624_190613.c:13: warning: incompatible implicit declaration of built-in function ‘printf’
Glibc header files and runtime system disagree on version.
Header files: x86-linux



That's somehow related to the glibc, right? So, which glibc does ubuntu come with? And am I able to compile with it?


Thanks for your help

 - Michael

---

### Post by d_weil_e on 2007-07-17
It looks like you need to install the g++ package.  That should have those pesky header files you need.

ex.  sudo apt-get install g++

If you're installing this for a class and your instructor insists on SICStus, try installing SICStus after installing the g++ package.

Otherwise, just install gprolog: sudo apt-get install gprolog
It works fine.

Or, SWI-Prolog: sudo apt-get install swi-prolog
This is supposedly nearly the same as SICStus.

Try opening up Synaptic and searching for prolog for some different options and other info.  They all should behave the same for the most part.  I've found minor differences in different versions.  It seems like the key to installing prolog is finding one that's well compatible with your operating system.

Good luck.  Oh, and sorry about the late reply.  Your class is probly half over. :-)

---

