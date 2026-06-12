---
title: "No rule to make target `install'"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Winters on 2006-10-14
Hi everybody!

Just installed Dapper Drake a couple of days ago (I might as well tell you that I am an absolute beginner using Linux) and now I was trying to install a desktop theme through the Terminal but I can's seem to use the ./configure command or the make install. I get a no rule to make target install message. Here is an example.

winters@winters-laptop:~/gtk-engine-experience-0.10.4$ sudo make install
make: *** No rule to make target `install'.  Stop.
winters@winters-laptop:~/gtk-engine-experience-0.10.4$

I would appreciate any suggestions..

Thanks

---

### Post by PriceChild on 2006-10-14
Please ensure that build-essential is installed.

Then, could you give us your first error... ie the configure command.

(would be useful to have a ls before to see contents of folder)

---

### Post by MasonM on 2006-10-14
Assuming you have the build-essentional package installed, the correct sequence is;

$./configure
$make
#sudo make install


I suspect that you skipped the make. Until you actually compile it using make there is nothing to install.

---

### Post by Winters on 2006-10-14
> **PriceChild said:**
> Please ensure that build-essential is installed.

Then, could you give us your first error... ie the configure command.

(would be useful to have a ls before to see contents of folder)
__________________________________________________________________

Hi there! Thanks for the reply! I pasted here the configure command and an  ls to the folder. I have used synaptics to download the build-essential package so I think i have it installed

winters@winters-laptop:~$ cd gtk-engine-experience-0.10.4
winters@winters-laptop:~/gtk-engine-experience-0.10.4$ ls
ac-helpers  ChangeLog   configure.ac  libtool      NEWS    TODO
aclocal.m4  config.log  COPYING       Makefile.am  README
AUTHORS     configure   INSTALL       Makefile.in  src
winters@winters-laptop:~/gtk-engine-experience-0.10.4$ ./configure checking for a BSD-compatible install... /usr/bin/install -c
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for bison... no
checking for byacc... no
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EXPERIENCE... configure: error: Package requirements (gtk+-2.0 >= 2.6.0 gdk-pixbuf-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EXPERIENCE_CFLAGS
and EXPERIENCE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

winters@winters-laptop:~/gtk-engine-experience-0.10.4$ make
make: *** No targets specified and no makefile found.  Stop.
winters@winters-laptop:~/gtk-engine-experience-0.10.4$

---

### Post by taurus on 2006-10-14
You need to install the developing packages for both gtk+-2.0 (gtk+-dev) & gdk-pixbuf-2.0 (gdk-pixbuf-dev)...

---

