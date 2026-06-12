---
title: "&quot;make&quot; command won't make"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-08-11
As am still trying my hand at source codes to get certain HW configured, I have seen the following happen.

I have upgraded to kernel 2.6.10, often asked for by the source codes. I now have the choice between two kernels at boot, so I boot into 2.6.10. 

As before, I can ./configure with no errors. But as soon a s I run "make" the thing fails with a long list of errors. I thought it was only for Alsa drivers that I am trying to install from source. But after fiddling with other sources, I still get the same thing. I've downloaded and installed a bunch of files that one of the Wiki's specified, (and other users suggested), but still I am unable to "make"

Any ideas?  I still have no sound and other users have used my thread to successfully get their sound up with the same hardware.

---

### Post by Knome_fan on 2005-08-11
Did you install build-essentials?
What error message are you getting specifically?
What hardware doesn't work exactly?

Edit: Also I don't think you will have much luck with installing new alsadrivers, as alsa is part of the kernel, but I might be wrong there.

---

### Post by GrootBrak on 2005-08-11
[QUOTE=Knome_fan]Did you install build-essentials?
What error message are you getting specifically?
What hardware doesn't work exactly?

Edit: Also I don't think you will have much luck with installing new alsadrivers, as alsa is part of the kernel, but I might be wrong there.[/QUOTE]
 Yes, I have build-essentials. 

Here is the error message. I am trying to install new alsa-drivers. I have no sound, I won't go into the detail of wh not, I have very long posts about it....
> 
root@HomePC:/home/jacques/alsa/alsa-driver-1.0.9b # make
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/jacques/alsa/alsa-driver-1.0.9b  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/jacques/alsa/alsa-driver-1.0.9b/acore/hpetimer.o
  CC [M]  /home/jacques/alsa/alsa-driver-1.0.9b/acore/memalloc.o
  CC [M]  /home/jacques/alsa/alsa-driver-1.0.9b/acore/sgbuf.o
  CC [M]  /home/jacques/alsa/alsa-driver-1.0.9b/acore/memory_wrapper.o
  CC [M]  /home/jacques/alsa/alsa-driver-1.0.9b/acore/pcm.o
copying file /home/jacques/alsa/alsa-driver-1.0.9b/core/pcm_native.c
cp: cannot stat `/home/jacques/alsa/alsa-driver-1.0.9b/core/pcm_native.c': No such file or directory
patch: **** Can't find file /home/jacques/alsa/alsa-driver-1.0.9b/acore/pcm_native.c : No such file or directory
  CC [M]  /home/jacques/alsa/alsa-driver-1.0.9b/acore/pcm_native.s
gcc: /home/jacques/alsa/alsa-driver-1.0.9b/acore/pcm_native.c: No such file or directory
gcc: no input files
make[3]: *** [/home/jacques/alsa/alsa-driver-1.0.9b/acore/pcm_native.s] Error 1
make[2]: *** [/home/jacques/alsa/alsa-driver-1.0.9b/acore] Error 2
make[1]: *** [_module_/home/jacques/alsa/alsa-driver-1.0.9b] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make: *** [compile] Error 2

The hardware in question is sound. Intel D915GEV motherboard, uses Intel HDA. Used he wiki link for installing Intel HDA, also the files  needed to compile etc. Nothing. I tried to compile some other programs from source as well, "make" won't make. Errors vary from program to program.

---

### Post by feydreva on 2005-10-25
I get the same can of error ...
Do someone have a solution ????

there are my logs....

make[1]: Entering directory `/home/feydreva/src/kernel-source-2.6.8'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.9b/acore/hpetimer.o
In file included from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /usr/src/alsa/alsa-driver-1.0.9b/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9b/include/sound/driver.h:42,
                 from /usr/src/alsa/alsa-driver-1.0.9b/acore/hpetimer.c:22:
include/asm/processor.h:87: error: array type has incomplete element type
In file included from /usr/src/alsa/alsa-driver-1.0.9b/include/adriver.h:677,
                 from /usr/src/alsa/alsa-driver-1.0.9b/include/sound/driver.h:42,
                 from /usr/src/alsa/alsa-driver-1.0.9b/acore/hpetimer.c:22:
include/linux/pci.h:778: error: syntax error before numeric constant
make[4]: *** [/usr/src/alsa/alsa-driver-1.0.9b/acore/hpetimer.o] Erreur 1
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.9b/acore] Erreur 2
make[2]: *** [_module_/usr/src/alsa/alsa-driver-1.0.9b] Erreur 2
make[1]: *** [modules] Erreur 2
make[1]: Leaving directory `/home/feydreva/src/kernel-source-2.6.8'
make: *** [compile] Erreur 2

---

