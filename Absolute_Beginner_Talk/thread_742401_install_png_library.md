---
title: "install png library"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by animalprimate on 2008-04-01
i got png library from source forge {bz2 version}
unzipped and stuff, then ./configured saw this:

--------------------------------------------------------------------------------------------------------------------

dungeonpsyche@dungeonpsyche-laptop:~/download/libpng-1.2.25$ ls
aclocal.m4     config.sub    libpng-1.2.25.txt  Makefile.am    pngerror.c  pngrtran.c   pngwtran.c
ANNOUNCE       configure     libpng.3           Makefile.in    pnggccrd.c  pngrutil.c   pngwutil.c
autogen.sh     configure.ac  libpng-config      missing        pngget.c    pngset.c     projects
CHANGES        contrib       libpng.pc          mkinstalldirs  png.h       pngtest.c    README
config.guess   depcomp       libpngpf.3         png.5          pngmem.c    pngtest.png  scripts
config.h       example.c     libtool            pngbar.jpg     pngnow.png  pngtrans.c   stamp-h1
config.h.in    INSTALL       LICENSE            pngbar.png     pngpread.c  pngvcrd.c    test-pngtest.sh
config.log     install-sh    ltmain.sh          png.c          pngread.c   pngwio.c     TODO
config.status  KNOWNBUG      Makefile           pngconf.h      pngrio.c    pngwrite.c   Y2KINFO

dungeonpsyche@dungeonpsyche-laptop:~/download/libpng-1.2.25$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking for a sed that does not truncate output... /bin/sed
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking how to run the C preprocessor... gcc -E
checking for sed... /bin/sed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
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
checking the maximum length of command line arguments... 98304
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
checking whether to build static libraries... yes
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
checking for ANSI C header files... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for working strtod... yes
checking for memset... yes
checking for pow... no
checking for pow in -lm... yes
checking for zlibVersion in -lz... yes
checking if assembler code in pnggccrd.c can be compiled without PNG_NO_MMX_CODE... yes
checking if libraries can be versioned... yes
checking for symbol prefix...
configure: pkgconfig directory is ${libdir}/pkgconfig
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libpng.pc
config.status: creating libpng-config
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

--------------------------------------------------------------------------------------------------------------------

then i try too configure cross-fire client and i see this

*configure: error: You must have the png library installed to compile the client*

**how come png librarys not installed?**:confused:

---

### Post by c-ron on 2008-04-01
```
sudo apt-get install libpng3
```

---

