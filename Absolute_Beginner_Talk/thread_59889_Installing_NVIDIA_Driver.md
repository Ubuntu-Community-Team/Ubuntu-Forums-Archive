---
title: "Installing NVIDIA Driver"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by Seb Spiers on 2005-08-25
I get the error message; "Unable to load kernel module 'nvidia.ko'."

Any ideas anyone? :)

---

### Post by zlogic on 2005-08-25
You probably don't have the nvidia-kernal-common package installed. Are you using Ubuntu's .deb or the original Nvidia's drivers?

---

### Post by Seb Spiers on 2005-08-25
I downloaded the latest driver from nvidia website.

---

### Post by tseliot on 2005-08-25
[QUOTE=Seb Spiers]I get the error message; "Unable to load kernel module 'nvidia.ko'."

Any ideas anyone? :)[/QUOTE]
Try my guide, it's easy (step by step)

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)

And post the complete output of the error:

you can find it under /var/log/ it's the nvidia log file

---

### Post by Seb Spiers on 2005-08-25
:)```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Aug 25 21:36:42 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.12-7-386/build'
-> Performing CC test with CC="cc".
-> gcc-version-check failed:
   
   You appear to be compiling the NVIDIA kernel module with a different compile
   r than the one that was used to compile the running kernel.  This may be fin
   e, but there are cases where this can lead to instability.  The compiler use
   d to compile the kernel was gcc 3.4; the current compiler is gcc 4.0.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
-> Performing rivafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.12-7-386/bu
   ild SYSOUT=/lib/modules/2.6.12-7-386/build'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.12-7-386/build SUBDIRS=/tmp
   /selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.tmp_vers
   ions
   make -f scripts/Makefile.build obj=/tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz8240/NVI
   DIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL_
   _ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -
   fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -m
   preferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i38
   6/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz
   8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wc
   har-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fn
   o-common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAME
   S -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERN
   EL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=767
   6  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AG
   PGART_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DN
   V_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT 
   -DMODULE -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz8240/
   NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz8240/NVIDIA-L
   inux-x86-1.0-7676-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
   /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv.c: In function 
   ‘nvidia_init_module’:
   /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv.c:1073: warning
   : ‘pm_register’ is deprecated (declared at include/linux/pm.h:106)
   /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv.c:1170: warning
   : ‘pm_unregister’ is deprecated (declared at include/linux/pm.h:111)
   /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv.c: In function 
   ‘nvidia_exit_module’:
   /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv.c:1227: warning
   : ‘pm_unregister’ is deprecated (declared at include/linux/pm.h:111)
     cc -Wp,-MD,/tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.nv-v
   m.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERN
   EL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasin
   g -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float
   -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm-i
   386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/self
   gz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-t
   ype -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-
   multichar  -Werror -O -fno-common -MD   -Wsign-compare -Wno-cast-qual -Wno-e
   rror -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODU
   LE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_M
   AJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -
   DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_RE
   MAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_
   PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BA
   SENAME=nv_vm -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz8240/NVIDIA-Linux-x86-
   1.0-7676-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7
   676-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.os-a
   gp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KER
   NEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasi
   ng -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-floa
   t -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude/asm
   -i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/se
   lfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv -Wall -
   Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare -
   Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM
   -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSIO
   N=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -DNDEBUG -DN
   V_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_REMAP_PFN_RAN
   GE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DN
   V_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_a
   gp -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-p
   kg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/
   usr/src/nv/os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.os-i
   nterface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -
   D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-
   aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointe
   r -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march
   =i386 -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-poi
   nter-sign -I/tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv -Wall 
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare 
   -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTR
   M -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERS
   ION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -DNDEBUG -
   DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_REMAP_PFN_R
   ANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -
   DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os
   _interface -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz8240/NVIDIA-Linux-x86-1.
   0-7676-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz8240/NVIDIA-Linux-x86-
   1.0-7676-pkg1/usr/src/nv/os-interfac
   e.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.os-r
   egistry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D
   __KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-a
   liasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft
   -float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclud
   e/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -I/t
   mp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv -Wall -Wimplicit -Wr
   eturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith
    -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare -Wno-cast-qual 
   -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE
   -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR
   _VERSION=0 -DNV_PATCHLEVEL=7676  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUC
   T_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DN
   V_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PC
   I_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_regis
   try -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-
   pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676
   -pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:864,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src
   /nv/os-registry.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:253: warning: wrong type argument to increment
     ld -m elf_i386  -r -o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/s
   rc/nv/nvidia.o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv-
   kernel.o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv.o /tmp
   /selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz824
   0/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/os-agp.o /tmp/selfgz8240/NVIDIA-
   Linux-x86-1.0-7676-pkg1/usr/src/nv/os-interface.o /tmp/selfgz8240/NVIDIA-Lin
   ux-x86-1.0-7676-pkg1/usr/src/nv/os-registry.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.12-7-386/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.12-7-386/Module.sy
   mvers /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nvidia.o
   Warning: could not find /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/s
   rc/nv/.nv-kernel.o.cmd for /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/us
   r/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/.nvid
   ia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D_
   _KERNEL__ -Iinclude  -Wall -Wstrict-prototypes -Wno-trigraphs -fno-strict-al
   iasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-
   float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i386 -Iinclude
   /asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign    -D
   KBUILD_BASENAME=nvidia -DKBUILD_MODNAME=nvidia -DMODULE -c -o /tmp/selfgz824
   0/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz8240/NVI
   DIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -r -o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/sr
   c/nv/nvidia.ko /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nvi
   dia.o /tmp/selfgz8240/NVIDIA-Linux-x86-1.0-7676-pkg1/usr/src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Invalid module format
-> Kernel messages:
   [4294727.951000] ACPI: Power Button (CM) [PWRB]
   [4294727.976000] Using specific hotkey driver
   [4294728.041000] ibm_acpi: ec object not found
   [4294728.277000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
   [4294728.277000] apm: overridden by ACPI.
   [4294729.955000] Bluetooth: L2CAP ver 2.7
   [4294729.955000] Bluetooth: L2CAP socket layer initialized
   [4294730.009000] Bluetooth: RFCOMM ver 1.5
   [4294730.009000] Bluetooth: RFCOMM socket layer initialized
   [4294730.009000] Bluetooth: RFCOMM TTY layer initialized
   [4294741.082000] NET: Registered protocol family 10
   [4294741.082000] Disabled Privacy Extensions on device c02eb280(lo)
   [4294741.082000] IPv6 over IPv4 tunneling driver
   [4294751.099000] eth0: no IPv6 routers present
   [4295721.216000] nvidia: version magic '2.6.12-7-386 386 gcc-4.0' should be
   '2.6.12-7-386 386 gcc-3.4'
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
```

---

### Post by tseliot on 2005-08-25
Ok, it's easy.

Type this before running nvidia installer:

CC=gcc-3.4 
export CC

then run the installer

---

### Post by Seb Spiers on 2005-08-26
[QUOTE=tseliot]Ok, it's easy.

Type this before running nvidia installer:

CC=gcc-3.4 
export CC

then run the installer[/QUOTE]
I have tried this and now I get;
```
gcc-version-check failed:

./usr/src/nv/conftest.shL line 9: gcc-3.4: command not found
Could not compile gcc-version-check.c

Abort Y/N?
```
If I select No I get the following;
```
ERROR: Unable to determine the VNIDIA kernel module filename.
```

---

### Post by tseliot on 2005-08-26
[QUOTE=Seb Spiers]I have tried this and now I get;
```
gcc-version-check failed:

./usr/src/nv/conftest.shL line 9: gcc-3.4: command not found
Could not compile gcc-version-check.c

Abort Y/N?
```
If I select No I get the following;
```
ERROR: Unable to determine the VNIDIA kernel module filename.
```[/QUOTE]
Open Synaptic or Kynaptic and make sure you have gcc-3.4 installed (not only the base package)

After the installation of gcc-3.4 repeat the process with the installer again

P.S. This is also written in my guide, please have a look

---

