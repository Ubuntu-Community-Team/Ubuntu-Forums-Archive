---
title: "sys/cdefs.h"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by mxsteini on 2007-05-31
Hi there,
I'm running linux for many years and today I feel like a bloody beginner:
simple C-programm:
#include <stdio.h>
main () { print("gues what");}

steini@steini0:~$ gcc hello.c
In file included from /usr/include/stdio.h:28,
                 from hello.c:1:
/usr/include/features.h:323:25: error: sys/cdefs.h: No such file or directory
In file included from /usr/include/stdio.h:34,

where is sys/cdefs.h ?
debian package-search says it must be in libc6-dev but not in feisty!

Where is it? And how do I get my gcc working?

Michael

---

