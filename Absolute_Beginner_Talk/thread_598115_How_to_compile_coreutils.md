---
title: "How to compile coreutils"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by jkchow on 2007-10-31
Hey all,

I'm freakin stuck. I'm an undergrad programmer that needs linux to compile some projects. One of my homework was to compile coreutils. I downloaded coreutils 6.7, ran ./configure and then make. However, i end up with this error message:

make  all-recursive
make[1]: Entering directory `/home/jkchow/Desktop/coreutils-5.97'
Making all in lib
make[2]: Entering directory `/home/jkchow/Desktop/coreutils-5.97/lib'
make  all-am
make[3]: Entering directory `/home/jkchow/Desktop/coreutils-5.97/lib'
if gcc -std=gnu99 -DHAVE_CONFIG_H -DLIBDIR=\"/usr/local/lib\" -I. -I. -I..  -I.. -I.   -g -O2 -MT utimecmp.o -MD -MP -MF ".deps/utimecmp.Tpo" -c -o utimecmp.o utimecmp.c; \
        then mv -f ".deps/utimecmp.Tpo" ".deps/utimecmp.Po"; else rm -f ".deps/utimecmp.Tpo"; exit 1; fi
In file included from utimecmp.c:41:
utimens.h:2: error: conflicting types for 'futimens'
/usr/include/sys/stat.h:370: error: previous declaration of 'futimens' was here
make[3]: *** [utimecmp.o] Error 1
make[3]: Leaving directory `/home/jkchow/Desktop/coreutils-5.97/lib'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/jkchow/Desktop/coreutils-5.97/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jkchow/Desktop/coreutils-5.97'
make: *** [all] Error 2
jkchow@jkchow-laptop:~/Desktop/coreutils-5.97$ 

Any help?

-John C.

---

