---
title: "[Comiling Issue] can't use make command"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by S1NGH on 2006-09-08
alright, so i have been trying to compile some packages in tar.bz2 (doesn't make a difference - its a sourcode) so anyway i am experiencing problems compiling all the source files i download.

here is my log:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether to enable maintainer-specific portions of Makefiles... no
checking for target architecture... i686-pc-linux-gnu
checking for some Win32 platform... no
checking for native Win32... no
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking whether to turn on debugging... no
checking whether to turn on profiling... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking whether time.h and sys/time.h may both be included... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/times.h usability... yes
checking sys/times.h presence... yes
checking for sys/times.h... yes
checking for sys/wait.h... (cached) yes
checking for unistd.h... (cached) yes
checking for pid_t... yes
checking return type of signal handlers... void
checking for vprintf... yes
checking for _doprnt... no
checking for working alloca.h... yes
checking for alloca... yes
checking for difftime... yes
checking for putenv... yes
checking for mmap... yes
checking whether binary relocation support should be enabled... no
checking for _NL_MEASUREMENT_MEASUREMENT... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
ravjeet@cyber-linux:~/Desktop/gimp-2.3.10/gimp-2.3.10$ mkae && make install
bash: mkae: command not found
ravjeet@cyber-linux:~/Desktop/gimp-2.3.10/gimp-2.3.10$ make && make install
make: *** No targets specified and no makefile found.  Stop.
ravjeet@cyber-linux:~/Desktop/gimp-2.3.10/gimp-2.3.10$ mkae
bash: mkae: command not found
ravjeet@cyber-linux:~/Desktop/gimp-2.3.10/gimp-2.3.10$ make
make: *** No targets specified and no makefile found.  Stop.
ravjeet@cyber-linux:~/Desktop/gimp-2.3.10/gimp-2.3.10$ sudo check install
Password:
sudo: check: command not found
ravjeet@cyber-linux:~/Desktop/gimp-2.3.10/gimp-2.3.10$  
```

i would appreciate it if someone can help me start compiling packages so that i may geeet files in the native .deb format :)

i think i have all the necessary installations to compile but the make command just blows me off...

---

### Post by Chickencha on 2006-09-08
You got a configure error:

```
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
```

Fix this and (assuming there are no more configuration errors) you should be able to make.

---

