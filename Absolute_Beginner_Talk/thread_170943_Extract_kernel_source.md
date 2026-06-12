---
title: "Extract kernel source"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2006-05-05
Hi,
i'm trying to install captiva (to access my ntfs-hdd), but when i try to ./configure it
and this is what it keeps giving me :( 
```
iarwain@Middle-Earth:~/Desktop/captive-static-1.1.7/fuse-2.5.3$ ./configure --with-kernel=/usr/src
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from  object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for fork... yes
checking for setxattr... yes
checking for fdatasync... yes
checking for struct stat.st_atim... yes
configure: creating ./config.status
config.status: creating fuse.pc
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating util/Makefile
config.status: creating example/Makefile
config.status: creating include/Makefile
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
configure: configuring in kernel
configure: running /bin/sh './configure' --prefix=/usr/local  '--with-kernel=/usr/src' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking kernel source directory... /usr/src
checking kernel build directory... /usr/src
checking kernel source version... Not found
configure: error:
        *** Cannot determine the version of the linux kernel source. Please
        *** prepare the kernel before running this script
configure: error: /bin/sh './configure' failed for kernel

```

Thanks,

EDIT: maybe a tad too little info :D
>    2. The kernel source must be prepared:

          o Extract the kernel source to some directory
          o Copy the running kernel's config (usually found in /boot/config-X.Y.Z) to .config at the top of the source tree
          o Run make prepare


So my question is: how do i extract my kernel source?

Iarwain

---

### Post by yabbadabbadont on 2006-05-05
Install the kernel source package through apt-get or synaptic.

The package you want is linux-source.

---

### Post by az on 2006-05-05
Install the linux-headers package for your kernel.  See what version of linux-image you are running and install the linux-headers package.

You should only use the source iof you want to recompile the kernel with differnet options.  You don't want to do that.

---

### Post by Iarwain ben-adar on 2006-05-05
> Package linux-headers is a virtual package provided by:
  linux-headers-2.6.10-6-k7-smp 2.6.10-34.17
  linux-headers-2.6.10-6-k7 2.6.10-34.17
  linux-headers-2.6.10-6-686-smp 2.6.10-34.17
  linux-headers-2.6.10-6-686 2.6.10-34.17
  linux-headers-2.6.10-6-386 2.6.10-34.17
  linux-headers-2.6.10-6 2.6.10-34.17
  linux-headers-2.6.10-5-k7-smp 2.6.10-34.7
  linux-headers-2.6.10-5-k7 2.6.10-34.7
  linux-headers-2.6.10-5-686-smp 2.6.10-34.7
  linux-headers-2.6.10-5-686 2.6.10-34.7
  linux-headers-2.6.10-5-386 2.6.10-34.7
  linux-headers-2.6.10-5 2.6.10-34.7
  linux-headers-2.6.11-1-k7-smp 2.6.11-0.2
  linux-headers-2.6.11-1-k7 2.6.11-0.2
  linux-headers-2.6.11-1-686-smp 2.6.11-0.2
  linux-headers-2.6.11-1-686 2.6.11-0.2
  linux-headers-2.6.11-1-386 2.6.11-0.2
  linux-headers-2.6.11-1 2.6.11-0.2


I know i have an 686, but what's the difference between "smp" and the normal ones? Wich one should i chose?


Iarwain

---

### Post by yabbadabbadont on 2006-05-05
sudo apt-get install linux-headers-`uname -r`

---

### Post by Iarwain ben-adar on 2006-05-05
Thanks! :D

now i can finally listen to my music ^^


Iarwain

---

### Post by zerhacke on 2006-05-05
[QUOTE=Iarwain ben-adar]I know i have an 686, but what's the difference between "smp" and the normal ones? Wich one should i chose?


Iarwain[/QUOTE]
SMP kernels are for computers that have more than one processer.

---

