---
title: "Problema audio. Incompatibilitat videos flash i aplicacions"
date: 2007-07-11
forum: Catalan Team
---

### Post by oksi on 2007-07-11
Hola, sóc un nou usuari del forum. Vinc citat pel canal del irc. 
Aquí us deixo el meu dubte:

No aconsegueixo arreglar el so amb el Ubuntu (Feisty 32 bits), resulta que tinc el clàssic problema de que si executo un video (youtube per exemple) no puc escoltar música amb un altre programa alhora i fins que no tanco el firefox no puc escoltar res, i viceversa tb. He trobat varies solucions per inet però no em funcionen :S vaig canviar el arxiu /etc/firefox/firefoxrc i vaig posar alsa-oss i auto i res de res, 
Si hi fico none no em funciona el so al firefox. Teniu alguna idea d'on puc trobar mes solucions?

arxiu /etc/firefox/firefoxrc :

# which /dev/dsp wrapper to use
FIREFOX_DSP="alsa-oss"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/bugs/29760](https://launchpad.net/bugs/29760).
export XLIB_SKIP_ARGB_VISUALS=1


Hardware:

**PB Asus M2N-E SLI ** (té tarja de so integrada amb chipset Nvidia Cmedia) vaig intentar baixar-me i instal·lar-me els drivers de la web d'asus pero quan executava el .run em donava el següent log d'error:

[COLOR="Red"]-perdó pel totxo[/COLOR]-


nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Tue Jul 10 14:40:40 2007

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
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-8)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.20-16-generic (root@terranova) (gcc
   version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007
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
   	KBUILD_EXTMOD="/tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main
   " -f /usr/src/linux-headers-2.6.20-16-generic/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.tmp_v
   ersions
   rm -f /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.tmp_vers
   ions/*
   make -f /usr/src/linux-headers-2.6.20-16-generic/scripts/Makefile.build obj=
   /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main
     cc -Wp,-MD,/tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.n
   valinux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D
   __KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.20-16-generic/i
   nclude -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-h
   eaders-2.6.20-16-generic/ubuntu/include  -I/tmp/selfgz30372/NFORCE-Linux-x86
   -1.0-0311-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs
   -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mprefer
   red-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -maccumulate-
   outgoing-args -I/usr/src/linux-headers-2.6.20-16-generic/include/asm-i386/ma
   ch-default -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g -fno-stac
   k-protector -Wdeclaration-after-statement -Wno-pointer-sign  -I/tmp/selfgz30
   372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main -Wall -Wimplicit -Wreturn-ty
   pe -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mu
   ltichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_CHANGE_PAGE_ATTR_PRESE
   NT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvalinux)"  -
   D"KBUILD_MODNAME=KBUIL
   D_STR(nvsound)" -c -o /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsoun
   d/main/.tmp_nvalinux.o /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsou
   nd/main/nvalinux.c
   In file included from include/linux/list.h:8,
                    from include/linux/module.h:10,
                    from /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsoun
   d/main/nvalinux.c:19:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: avís: pointer of type ‘void *’ used in ari
   thmetic
     cc -Wp,-MD,/tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.n
   vmixer.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D_
   _KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.20-16-generic/in
   clude -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-he
   aders-2.6.20-16-generic/ubuntu/include  -I/tmp/selfgz30372/NFORCE-Linux-x86-
   1.0-0311-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs 
   -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mre
   gparm=3 -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestandi
   ng -maccumulate-outgoing-args -I/usr/src/linux-headers-2.6.20-16-generic/inc
   lude/asm-i386/mach-default -Iinclude/asm-i386/mach-default -fomit-frame-poin
   ter -g -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign 
   -I/tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main -Wall -Wimpli
   cit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointe
   r-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_CHANGE_
   PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_ST
   R(nvmixer)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /tmp/selfgz30372/N
   FORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.tmp_nvmixer.o /tmp/selfgz30372/N
   FORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvmixer.c
   In file included from include/linux/list.h:8,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:59,
                    from /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsoun
   d/main/nvhw.h:29,
                    from /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsoun
   d/main/nvmixer.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: avís: pointer of type ‘void *’ used in ari
   thmetic
     cc -Wp,-MD,/tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.n
   vmain.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__
   KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.20-16-generic/inc
   lude -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-hea
   ders-2.6.20-16-generic/ubuntu/include  -I/tmp/selfgz30372/NFORCE-Linux-x86-1
   .0-0311-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -
   fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferr
   ed-stack-boundary=2 -march=i586 -mtune=generic -ffreestanding -maccumulate-o
   utgoing-args -I/usr/src/linux-headers-2.6.20-16-generic/include/asm-i386/mac
   h-default -Iinclude/asm-
   i386/mach-default -fomit-frame-pointer -g -fno-stack-protector -Wdeclaration
   -after-statement -Wno-pointer-sign  -I/tmp/selfgz30372/NFORCE-Linux-x86-1.0-
   0311-pkg1/nvsound/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wch
   ar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -W
   no-cast-qual -Wno-error -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR
   (s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvmain)"  -D"KBUILD_MODNAME=KBUILD_STR
   (nvsound)" -c -o /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/mai
   n/.tmp_nvmain.o /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main
   /nvmain.c
   In file included from include/linux/list.h:8,
                    from include/linux/module.h:10,
                    from /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsoun
   d/main/nvmain.c:27:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: avís: pointer of type ‘void *’ used in ari
   thmetic
   /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvmain.c: In fu
   nction ‘Nvaudio_mmap’:
   /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvmain.c:991: a
   vís: implicit declaration of function ‘remap_page_range’
   /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvmain.c: In fu
   nction ‘Nvaudio_probe’:
   /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvmain.c:2091: 
   avís: passing argument 2 of ‘request_irq’ from incompatible pointer typ
   e
   /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvmain.c:2179: 
   avís: passing argument 2 of ‘request_irq’ from incompatible pointer typ
   e
   /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvmain.c: En el
   nivell principal:
   /tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvmain.c:2205: 
   error: expected ‘)’ before string constant
   make[4]: *** [/tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/n
   vmain.o] Error 1
   make[3]: *** [_module_/tmp/selfgz30372/NFORCE-Linux-x86-1.0-0311-pkg1/nvsoun
   d/main] Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).

---

