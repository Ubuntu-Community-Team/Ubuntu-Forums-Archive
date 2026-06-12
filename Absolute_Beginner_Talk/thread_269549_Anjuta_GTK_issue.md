---
title: "Anjuta GTK issue"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-01
Hello fellow Ubuntu-ers...
I am trying to install any C++ capable IDE that I can find for free and I keep running into the same problem when I try to do ./configure....

root@stubbornpc:~/anjuta-2.0.2# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for library containing strerror... none required
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
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
checking return type of signal handlers... void
checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GOBJECT... yes
checking for GMODULE... yes
checking for GTHREAD... yes
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@stubbornpc:~/anjuta-2.0.2#    

I have been to GTK.org and tried downloading the RPM, but it was broken or corrupted somehow. Is there a simpler way to get a "quick and dirty" IDE for Linux.  I just want to do my C++ homework!!](*,)

---

### Post by uk_sphinx on 2006-10-01
is that one you downloaded from synaptic packet manager?

---

### Post by saintj0n on 2006-10-02
I couldn't find that one in synaptic package manager. I downloaded the tarball and went from there. I'm starting to think maybe I should find something that doesn't require GTK if possible.  This is all new to me, so I don't know what my options are.:-k

---

### Post by uk_sphinx on 2006-10-02
have you enabled the extra repositries??
your search might be successfull then.
i have downloaded the python ide when i enabled them.
it works great.
im sure there might be one in there.

---

### Post by Marsolin on 2006-10-02
[Anjuta]("http://linuxappfinder.com/package/anjuta") is definitely in the extra Ubuntu repositories. Version 1.2.4 is in dapper and 2.0.2 is in edgy.

---

### Post by saintj0n on 2006-10-02
I have tried installing extra repositories and I am consistently running into this error:

E: python2.3-4suite: subprocess post-installation script returned error exit status 2

It seems to pop up only on certain GTK related packages.  :confused:

---

### Post by saintj0n on 2006-10-02
Ok...
Anjuta *is* working, despite the weird error message. Thanks...:???:

---

