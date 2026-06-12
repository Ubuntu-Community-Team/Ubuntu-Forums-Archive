---
title: "Ndiswrapper: Make compile errors"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by shida on 2008-02-18
Trying to install ndiswrapper-1.52 with wpa on Dapper. When I enter the make command in the ndiswrapper directory, I get the following error below. Have been searching all day for a solution, so if anyone can point me in the right direction, I would be very grateful. 

shida@shida-comp:~/Desktop/ndiswrapper-1.52$ make
make -C driver
make[1]: Entering directory `/home/shida/Desktop/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.15-51-386 SUBDIRS=/home/shida/Desktop/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-51-386'
  CC [M]  /home/shida/Desktop/ndiswrapper-1.52/driver/crt.o
In file included from /home/shida/Desktop/ndiswrapper-1.52/driver/crt.c:16:
/home/shida/Desktop/ndiswrapper-1.52/driver/ntoskernel.h:720: error: field ‘lock’ has incomplete type
/home/shida/Desktop/ndiswrapper-1.52/driver/ntoskernel.h: In function ‘raise_irql’:
/home/shida/Desktop/ndiswrapper-1.52/driver/ntoskernel.h:757: warning: implicit declaration of function ‘mutex_lock’
/home/shida/Desktop/ndiswrapper-1.52/driver/ntoskernel.h: In function ‘lower_irql’:
/home/shida/Desktop/ndiswrapper-1.52/driver/ntoskernel.h:779: warning: implicit declaration of function ‘mutex_unlock’
make[3]: *** [/home/shida/Desktop/ndiswrapper-1.52/driver/crt.o] Error 1
make[2]: *** [_module_/home/shida/Desktop/ndiswrapper-1.52/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-51-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/shida/Desktop/ndiswrapper-1.52/driver'
make: *** [all] Error 2

---

### Post by aysiu on 2008-02-18
Any reason you're compiling from source?

The [*ndiswrapper* in the repositories](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils) appears to be 1.8.

---

