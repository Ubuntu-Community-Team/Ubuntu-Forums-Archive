---
title: "installing gtk"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by berna1111 on 2007-11-28
```
berna1111@berna1111-laptop:~$ cd Desktop
berna1111@berna1111-laptop:~/Desktop$ cd pyorbit-2.14.3berna1111@berna1111-laptop:~/Desktop/pyorbit-2.14.3$ ls
aclocal.m4         configure     libtool      NEWS             setup.py
AUTHORS            configure.in  ltmain.sh    PKG-INFO         src
ChangeLog          COPYING       m4           PKG-INFO.in      tests
ChangeLog.pre-2-0  depcomp       MAINTAINERS  py-compile       TODO
config.guess       dsextras.py   Makefile.am  pyorbit-2.pc.in
config.h.in        examples      Makefile.in  pyorbit.spec
config.log         INSTALL       MANIFEST.in  pyorbit.spec.in
config.sub         install-sh    missing      README
berna1111@berna1111-laptop:~/Desktop/pyorbit-2.14.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... found
checking for python libraries... -L/usr/lib -lm -lpthread -ldl  -lutil -lpython2.5
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYORBIT... configure: error: Package requirements (ORBit-2.0 >= 2.12) were not met:

No package 'ORBit-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYORBIT_CFLAGS
and PYORBIT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

berna1111@berna1111-laptop:~/Desktop/pyorbit-2.14.3$ make
make: *** Nenhum alvo indicado e nenhum arquivo make encontrado.  Pare.
berna1111@berna1111-laptop:~/Desktop/pyorbit-2.14.3$ ls

```
Well, whether I'm really dumb or this doesn't work properly on my computer...
I hope it's the first one...
Can anyone tell what I'm doing wrong?
Sorry for the trouble....

---

### Post by aysiu on 2007-11-28
Have you tried this? ```
sudo apt-get update
sudo apt-get install python-pyorbit
```

---

