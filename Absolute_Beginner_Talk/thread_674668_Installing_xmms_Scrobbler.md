---
title: "Installing xmms Scrobbler"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-01-21
I'm sorry but I'm absolutely new to Linux and Ubuntu in general and I've read the install file and Readme file and basically all the files it comes with and I have no idea how to install it.  I've opened my terminal and did the commands it asked for:

```
./configure
	make
	make install
```

I've done all of those but when my ./configure finishes, this is what it tells me:

> checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking how to run the C preprocessor... gcc -E
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
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
checking whether byte ordering is bigendian... no
checking for long... yes
checking size of long... 4
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking wchar.h usability... yes
checking wchar.h presence... yes
checking for wchar.h... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking if XMMS plugin is to be built... yes
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: WARNING: *** GLIB >= 1.2.2 not installed - please install first ***
checking for xmms-config... no
checking for XMMS - version >= 1.2.4... no
*** The xmms-config script installed by XMMS could not be found.
*** If XMMS was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XMMS_CONFIG environment variable to the
*** full path to xmms-config.
configure: WARNING: *** XMMS >= 1.2.4 not installed - please install first ***
checking if BMP plugin is to be built... checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
yes
checking for GTK... yes
checking for BMP... no
configure: WARNING: *** BMP >= 0.9.7rc2 not installed - please install first ***
configure: error: No media player specified, or none found. Cannot build.


Then I try to do the make command and it gives me this:

> make: *** No targets specified and no makefile found.  Stop.

Could someone tell me what I'm doing wrong?

Also, I do have xmms 1.2.10 installed.  I dunno if there's anything else I need.



Please help!

---

### Post by emarkd on 2008-01-21
You don't have to build that from source.  It's in the repositories.  From the command line run
```

sudo apt-get install xmms2-scrobbler
```

---

### Post by ladybumavere on 2008-01-21
> **emarkd said:**
> You don't have to build that from source.  It's in the repositories.  From the command line run
```

sudo apt-get install xmms2-scrobbler
```

Wow, that worked very easily and did not give me any error messages.  New question, how do I operate it or configure it?  I looked in the preferences of xmms and couldn't find anything about it.  Any help here?

Sorry of the ignorance. :oops:

---

### Post by emarkd on 2008-01-21
Never used it, so I can't help here.  Glad we got your installation issues worked out, though.  Good luck and have fun.

---

### Post by ladybumavere on 2008-01-21
> **emarkd said:**
> Never used it, so I can't help here.  Glad we got your installation issues worked out, though.  Good luck and have fun.



Thanks a lot, I do appreciate the help!

---

