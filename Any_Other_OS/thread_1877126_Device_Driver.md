---
title: "Device Driver"
date: 2011-11-07
forum: Any Other OS
---

### Post by ashwinshakti on 2011-11-07
Hi, I have created nothig.c on ubuntu

#include <linux/module.h>
 MODULE_LICENSE("Dual BSD/GPL");

and make file
obj-m := nothing.o

and then 

# make -C /usr/src/linux-headers-2.6.38-8-generic M=pwd modules
getting output

make: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
scripts/Makefile.build:44: /usr/src/linux-headers-2.6.38-8-generic/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.38-8-generic/pwd/Makefile'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'


whats wrong in the creation, could u help me,

---

