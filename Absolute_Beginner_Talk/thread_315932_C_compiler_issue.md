---
title: "C compiler issue"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by transit_stop on 2006-12-09
Ok. new to all of this, but trying hard to get a grip on linux.. 

I am trying to compile a program..and doing ./configure tells me..
----------------------------
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
--------------------------------------

I am not able to make much of the config.log


I did do a find for *gcc* which I thought is the C compiler and it showed this...
------------------------------------
/usr/bin/gcc-4.0
/usr/bin/gccbug-4.0
/usr/bin/gcc-3.3
/usr/bin/i486-linux-gnu-gcc-4.0
/usr/bin/gccbug-3.3
/usr/bin/i486-linux-gnu-gcc-3.3
/usr/lib/gcc
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mcpp_gcc40_predef_old.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/mcpp_gcc40_predef_std.h
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libgcc.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libgcc_eh.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/64/libgcc_s.so
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcc.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcc_eh.a
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcc_s_64.so
/usr/lib/gcc/i486-linux-gnu/4.0.3/libgcc_s.so
------------------------------------------------------

I did export /usr/lib and /usr/bin to $PATH.

So not sure what I should be doing next....

---

### Post by IYY on 2006-12-09
Ubuntu does not install the compiler by default, but you can get it with the following command:

```
sudo apt-get install build-essential
```

It will get it from the internet repositories, or from the CD if one is inserted.

---

### Post by transit_stop on 2006-12-09
Thanks. That helped

---

