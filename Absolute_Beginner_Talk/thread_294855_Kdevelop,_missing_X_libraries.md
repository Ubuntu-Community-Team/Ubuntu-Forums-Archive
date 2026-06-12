---
title: "Kdevelop, missing X libraries"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-11-07
I'm getting the following error when trying to compile/build a KDE application (scroll down!):

```
cd '/home/felipe/KdevProjects/kdeapp1' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/felipe/KdevProjects/kdeapp1/debug' && cd '/home/felipe/KdevProjects/kdeapp1/debug' && CXXFLAGS="-O0 -g3" "/home/felipe/KdevProjects/kdeapp1/configure" --enable-debug=full && cd '/home/felipe/KdevProjects/kdeapp1/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
This Makefile is only for the CVS repository
This will be deleted before making the distribution

*** Creating acinclude.m4
*** Creating list of subdirectories
*** Creating configure.in
*** Creating aclocal.m4
*** Creating configure
*** Creating config.h template
*** Creating Makefile templates
*** Postprocessing Makefile templates
*** Creating date/time stamp
*** Finished
Don't forget to run ./configure
If you haven't done so in a while, run ./configure --help
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
installing -c
checking for -p flag to install... yes
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
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -fno-builtin... yes
checking whether g++ supports -Woverloaded-virtual... yes
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking whether accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
compiling yes (gcc)
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
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
compiling yes (g++)
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... 
configure: error: Can't find X libraries. Please check your installation and add the correct paths!
*** Exited with status: 1 ***

```

I installed libx11-dev and problem persists, not sure what other libraries I should install, or if I need to create a link to the libraries.
I'll appreciate any help!;) 

Thanks.

---

### Post by Ecthelion on 2006-11-07
Dunno of this helps but when I read about your problem, I'm wondering where the ./configure file goes looking for your X-libs...

So locating your X-libs and looking if the config file looks at the right place might help...

```
sudo locate -u
locate <name of the lib>
```

If the ./configure file doesn't look at the right place you might have to make a symbolic link at the place where your ./configure does look to the place where your x-libs actually are.

The code to make a symbolic link is
```
ln -s <place where the link refers to>
```
First you have to 'cd' to the right folder of course...

---

### Post by Dual Cortex on 2006-11-07
> **Ecthelion said:**
> Dunno of this helps but when I read about your problem, I'm wondering where the ./configure file goes looking for your X-libs...

So locating your X-libs and looking if the config file looks at the right place might help...

```
sudo locate -u
locate <name of the lib>
```

If the ./configure file doesn't look at the right place you might have to make a symbolic link at the place where your ./configure does look to the place where your x-libs actually are.

The code to make a symbolic link is
```
ln -s <place where the link refers to>
```
First you have to 'cd' to the right folder of course...


How do I find out where ./configure is looking for the libraries?
Thanks for the help! :)

---

### Post by Ecthelion on 2006-11-07
> How do I find out where ./configure is looking for the libraries?
Thanks for the help! 

Why not looking in the file itself?
You can open the ./configure file with any tekst-editor...

Then search for the name of the lib that is reported missing...


But are you really sure that the correct lib is installed?
Because those ./configure usually use your system's search function to search your disks for the correct application...
And if they don't find, you most likely wont find it either...

My guess is that you still miss the correct lib.
(I must say that I sometimes have troubles knowing which lib I exactly need too... Mostly I try to install all libs that are a bit related to it and then the problem gets solved, so I can't really tell you what lib you need...)

---

### Post by Dual Cortex on 2006-11-07
Got it fixed. I was missing the kde4libs-dev library, just as you somewhat suspected.
Should have checked out the suggested libraries to install before!
Thanks anyway!

---

