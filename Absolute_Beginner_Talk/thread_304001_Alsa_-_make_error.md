---
title: "Alsa - make error"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by addict3d on 2006-11-21
Ok first up. my apologies if this is in the wrong forum. 

I am trying to compile alsa 1.0.13 from source. My sound card is via 82C686. OS is ubuntu edgy

well " ./configure --with-cards=via82xx " succeeds. But make fails, the error being something in memalloc.o . The error part of amke output is 

> make -C /lib/modules/2.6.18.3-hacked/source SUBDIRS=/usr/src/alsa-driver-1.0.13 O=/lib/modules/2.6.18.3-hacked/build CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-2.6.18.3'

  WARNING: Symbol version dump /usr/src/linux-2.6.18.3/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /usr/src/alsa-driver-1.0.13/acore/memalloc.o
/bin/sh: scripts/genksyms/genksyms: No such file or directory
make[4]: *** [/usr/src/alsa-driver-1.0.13/acore/memalloc.o] Error 1
make[3]: *** [/usr/src/alsa-driver-1.0.13/acore] Error 2
make[2]: *** [_module_/usr/src/alsa-driver-1.0.13] Error 2
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18.3'
make: *** [compile] Error 2


Any help would be really appreciated. I have been searching all over the net to solve this. But no solution works. ](*,)  

Additional info : I built my kernel from 2.6.18.3 source, and screwed something in the inbuilt alsa modules so that there is no sound now( and hence i decided to install alsa from source, having read that its a solution somewhere on internet). But apart from sound the custom kernel works fine.

Thanks a lot

---

