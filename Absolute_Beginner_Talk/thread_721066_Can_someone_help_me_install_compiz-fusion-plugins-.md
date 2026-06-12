---
title: "Can someone help me install compiz-fusion-plugins-main-0.5.2"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Lord Xeb on 2008-03-11
So far I have followed every piece of help that I ca find, and so far, none has helped. I have done everything that each source gave me to install a tar.gz, but none of them helped. Here is what I have so far:
[PHP] xeb@nathan-laptop:~$ cd /home/nathan/Desktop/compiz-fusion-plugins-main-0.5.2
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ ./configure

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
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
checking for stdlib.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for intltool >= 0.35.0... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether byte ordering is bigendian... no
configure: Using PKG_CONFIG_PATH=NONE/lib/pkgconfig
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ... configure: error: Package requirements (compiz) were not met:

Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libxml-2.0', required by 'compiz', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables COMPIZ_CFLAGS
and COMPIZ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ 
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ make
make: *** No targets specified and no makefile found.  Stop.
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ /make
bash: /make: No such file or directory
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ ./make
bash: ./make: No such file or directory
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ sudo make
make: *** No targets specified and no makefile found.  Stop.
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ make install
make: *** No rule to make target `install'.  Stop.
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ sudo check
sudo: check: command not found
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ make clean
make: *** No rule to make target `clean'.  Stop.
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ /clean
bash: /clean: No such file or directory
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ clean
The program 'clean' is currently not installed.  You can install it by typing:
sudo apt-get install smarteiffel
bash: clean: command not found
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ cd pkg
bash: cd: pkg: No such file or directory
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ pkg
bash: pkg: command not found
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ ls
aclocal.m4         configure.ac         intltool-merge      missing
AUTHORS            COPYING              intltool-merge.in   mkinstalldirs
ChangeLog          data                 intltool-update     NEWS
compiz-text.pc.in  depcomp              intltool-update.in  po
config.guess       include              libtool             README
config.h.in        INSTALL              ltmain.sh           src
config.log         install-sh           Makefile.am         TODO
config.sub         intltool-extract     Makefile.in         VERSION
configure          intltool-extract.in  metadata
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ su
Password: 
su: Authentication failure
Sorry.
xeb@nathan-laptop:~/Desktop/compiz-fusion-plugins-main-0.5.2$ su
Password: 
root@nathan-laptop:/home/nathan/Desktop/compiz-fusion-plugins-main-0.5.2# make install
make: *** No rule to make target `install'.  Stop.
root@nathan-laptop:/home/nathan/Desktop/compiz-fusion-plugins-main-0.5.2# make
make: *** No targets specified and no makefile found.  Stop.
root@nathan-laptop:/home/nathan/Desktop/compiz-fusion-plugins-main-0.5.2# 

[/PHP]

I am lost. Can someone give me a pointer.

So far I have used these to help figure it out:
[http://ubuntuforums.org/archive/index.php/t-2356.htm]("http://ubuntuforums.org/archive/index.php/t-2356.htm")
[http://ubuntuforums.org/archive/index.php/t-2356.htm]("http://ubuntuforums.org/archive/index.php/t-2356.htm")
[http://mandrivausers.org/index.php?showtopic=10615]("http://mandrivausers.org/index.php?showtopic=10615")

---

### Post by jken146 on 2008-03-11
No need for source files.  That package is in the repositories: [http://packages.ubuntu.com/gutsy/compiz-fusion-plugins-main](http://packages.ubuntu.com/gutsy/compiz-fusion-plugins-main)

If you have Ubuntu 7.10 (Gutsy Gibbon) then all you have to do is install the package **compizconfig-settings-manager** -- this can be done in Add/Remove, Synaptic or at the terminal by typing ```
sudo aptitude install compizconfig-settings-manager
```

Then you go to System -> Preferences -> Advanced Desktop Effects and enable the plugins you want.

---

### Post by bluewraith on 2008-03-11
If you go to System > Admin > Synaptic Package Manager you can find that very package you are trying to install from source. Click it, click "Mark for installation", and then click "Apply"  and it will install the package along with its dependencies for you.

Why are you trying to install it from source?

---

### Post by perce on 2008-03-11
It looks like compiz-plugins-main is in the repository. Have you tried 

sudo apt-get install compiz-plugins-main

instead of compiling from source?

---

### Post by Lord Xeb on 2008-03-12
I tried that and it comes up with:


[PHP]xeb@nathan-laptop:~$ sudo apt-get install compiz-plugins-main
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-plugins-main
xeb@nathan-laptop:~$ 

[/PHP]

---

### Post by Lord Xeb on 2008-03-12
Never mind, I got it. It human error, not software.

---

