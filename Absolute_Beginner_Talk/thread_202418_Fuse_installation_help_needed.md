---
title: "Fuse installation help needed"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by fdrake on 2006-06-23
I am trying to install Fuse. I have downloaded v.2.5.3. When I try to configure it I have an errore message at the bottom:

# ./configure --with-kernel=SRCDIR
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
configure: running /bin/sh './configure' --prefix=/usr/local  '--with-kernel=SRCDIR' --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking kernel source directory... SRCDIR
checking kernel build directory... SRCDIR
checking kernel source version... Not found
configure: error:
        *** Cannot determine the version of the linux kernel source. Please
        *** prepare the kernel before running this script
configure: error: /bin/sh './configure' failed for kernel

---

### Post by David_T on 2006-06-24
Hello,
   You need to apt-get module-assistant.  It walks you through the steps of downloading kernel headers for your kernel version, selecting the kernel module you wish to install, everything up through creating the module as a package that is accessible/removable via apt.  
   The program is invoked w/out arguments, and it's got a console-based graphical interface.

---

