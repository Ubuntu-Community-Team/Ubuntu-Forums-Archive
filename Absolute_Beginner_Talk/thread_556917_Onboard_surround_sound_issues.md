---
title: "Onboard surround sound issues"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by dcj on 2007-09-21
Greetings,

I've recently installed Ubuntu for the first time alongside Windows XP. I have an Epox 8RDA+ motherboard with an AMD2500+ processor. The motherboard has an NForce2 chipset with onboard 6 channel surround. 

I have a 5.1 surround system. It works perfectly fine in Windows, but only the front 2 speakers work in linux. I tried following the instructions found [here:]("http://ubuntuforums.org/showthread.php?t=96370")

However, when I downloaded and tried to install the drivers from the NVIDIA website, the installer loaded up correctly but I got the following errors:

*No precompiled kernel interface was found to match your kernel; this means thatthe installer will need to compile a new kernel interface. " (ok)

"ERROR: You do not appear to have libc header files installed on your system. Please install your distribution's libc development package." (ok)

"ERROR: Installation of the audio driver has failed. Please see the file '/var/log/nvidia-nforce-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com" (ok)

Here are the details of the log file:
*****************
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sat Sep 22 13:30:28 2007

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86
-> Found package NVIDIA network driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.20-16-generic (root@terranova) (gcc
   version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.20-16-generic/build'
-> Kernel output path: '/lib/modules/2.6.20-16-generic/build'
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
***************
Any help would be greatly appreciated. I've been trying and searching for quite a while to find answers. Note that the network driver works fine - I selected not to install it for now in case it does something to my network connection in the meantime. It's just getting all my speakers to work in linux, rather than just the front 2, which is the problem.

---

### Post by alienexplorers on 2007-09-21
You need the following program file:
> sudo apt-get install build-essential

---

### Post by dcj on 2007-09-22
Thanks; got one step further but unfortunately still didn't work. It brought up a "building kernel module" screen but then gave an error that the kernel module was not created. - but didn't exactly say why.

The log:
**********************
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sat Sep 22 14:34:39 2007

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86
-> Found package NVIDIA network driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.20-16-generic (root@terranova) (gcc
   version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.20-16-generic/build'
-> Kernel output path: '/lib/modules/2.6.20-16-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.20-16-generic/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.20-16-gen
   eric/build SYSOUT=/lib/modules/2.6.20-16-generic/build'...
   make -C /lib/modules/2.6.20-16-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.20-16-generic \
   	KBUILD_EXTMOD="/tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main"
   -f /usr/src/linux-headers-2.6.20-16-generic/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_ve
   rsions
   rm -f /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_versi
   ons/*
   make -f /usr/src/linux-headers-2.6.20-16-generic/scripts/Makefile.build obj=
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     cc -Wp,-MD,/tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.nv
   alinux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D_
   _KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.20-16-generic/in
   clude -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-he
   aders-2.6.20-16-generic/ubuntu/include  -I/tmp/selfgz8816/NFORCE-Linux-x86-1
   .0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -
   fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferr
   ed-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -maccumulate-o
   utgoing-args -I/usr/src/linux-headers-2.6.20-16-generic/include/asm-i386/mac
   h-default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fno-stack
   -protector -Wdeclaration-after-statement -Wno-pointer-sign  -I/tmp/selfgz881
   6/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wimplicit -Wreturn-type
   -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multi
   char -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_CHANGE_PAGE_ATTR_PRESENT 
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvalinux)"  -D"K
   BUILD_MODNAME=KBUILD_STR(n
   vsound)" -c -o /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.
   tmp_nvalinux.o /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/n
   valinux.c
   In file included from include/linux/list.h:8,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound
   /main/nvalinux.c:19:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.nv
   mixer.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__
   KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.20-16-generic/inc
   lude -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-hea
   ders-2.6.20-16-generic/ubuntu/include  -I/tmp/selfgz8816/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -f
   no-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -m
   preferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -maccum
   ulate-outgoing-args -I/usr/src/linux-headers-2.6.20-16-generic/include/asm-i
   386/mach-default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fn
   o-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign  -I/tmp/se
   lfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -W
   no-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_CHANGE_PAGE_ATTR_
   PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvmixer)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /tmp/selfgz8816/NFORCE-Linux
   -x86-1.0-0310-pkg1/nvsound/main/.tmp_nvmixer.o /tmp/selfgz8816/NFORCE-Linux-
   x86-1.0-0310-pkg1/nvsound/main/nvmixer.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound
   /main/nvhw.h:29,
                    from /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound
   /main/nvmixer.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.nv
   main.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__K
   ERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.20-16-generic/incl
   ude -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-head
   ers-2.6.20-16-generic/ubuntu/include  -I/tmp/selfgz8816/NFORCE-Linux-x86-1.0
   -0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred
   -stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -maccumulate-out
   going-args -I/usr/src/linux-headers-2.6.20-16-generic/include/asm-i386/mach-
   default -Iinclude/asm-i386/mach-defau
   lt -fomit-frame-pointer -g -fno-stack-protector -Wdeclaration-after-statemen
   t -Wno-pointer-sign  -I/tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsoun
   d/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -W
   parentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wn
   o-error -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUIL
   D_BASENAME=KBUILD_STR(nvmain)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_nvmain.o /t
   mp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c
   In file included from include/linux/list.h:8,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound
   /main/nvmain.c:27:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c: In fun
   ction ‘Nvaudio_mmap’:
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c:991: wa
   rning: implicit declaration of function ‘remap_page_range’
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c: In fun
   ction ‘Nvaudio_probe’:
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c:2077: w
   arning: passing argument 2 of ‘request_irq’ from incompatible pointer ty
   pe
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c:2165: w
   arning: passing argument 2 of ‘request_irq’ from incompatible pointer ty
   pe
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c: At top
   level:
   /tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c:2191: e
   rror: expected ‘)’ before string constant
   make[4]: *** [/tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nv
   main.o] Error 1
   make[3]: *** [_module_/tmp/selfgz8816/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound
   /main] Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
**************************

---

