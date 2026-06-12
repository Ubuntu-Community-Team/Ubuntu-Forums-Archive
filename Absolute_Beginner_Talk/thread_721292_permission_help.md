---
title: "permission help"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Andeh on 2008-03-11
First of all, apologies if this problem has been resolved elsewhere on the forums but i've been unable to find it. My Problem is simple, i installed Unbuntu 7.10 The Gutsy Gibbon to run a duel boot system with XP on the hope i can rid myself of the evils of Microsoft once and for all.

I've been pottering about getting my graphics card installed and my soundcard etc etc, i've been having a problem with installing things in the conlsole. The item i'm trying to install is for the g15 keyboard support only, i keep getting a message saying i don't have permission  to "make install" for libg15-1.2.6.

this is the output i get for both the ./configure and make install commands

```
andeh@Pinkee:~/Desktop/libg15-1.2.6$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for main in -lusb... yes
checking for ANSI C header files... (cached) yes
checking for string.h... (cached) yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking for an ANSI C-conforming const... yes
checking for memset... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```

and 

```
andeh@Pinkee:~/Desktop/libg15-1.2.6$ make install
make[1]: Entering directory `/home/andeh/Desktop/libg15-1.2.6'
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libg15.la' '/usr/lib/libg15.la'
/usr/bin/install -c .libs/libg15.so.1.0.0 /usr/lib/libg15.so.1.0.0
/usr/bin/install: cannot create regular file `/usr/lib/libg15.so.1.0.0': Permission denied
make[1]: *** [install-libLTLIBRARIES] Error 1
make[1]: Leaving directory `/home/andeh/Desktop/libg15-1.2.6'
make: *** [install-am] Error 2

```

i hope someone can help

thanks

andy

---

### Post by jken146 on 2008-03-11
Type ```
sudo make install
``` instead.

---

### Post by Andeh on 2008-03-11
you are a god send! what exactly does that sudo bit mean anyway?

---

### Post by forrestcupp on 2008-03-11
The reason you have to type sudo first is because it is trying to install files to directories where only root has write privileges.  If you were building a program that only installed files in your /home directory, you wouldn't need the sudo.  But most things you compile will need that.

You don't need sudo when you run ./configure because it writes the configuration file in that same directory which is probably in your /home directory.  Your user account already has write privileges.

Sudo just puts you in root mode for that one command.

---

### Post by Andeh on 2008-03-11
its solved a few of my problems, i've figured out how to edit xorg.conf in the console using the sudo thing now :) so thank you guys so so much!

next on the list, get my mouse working properly hehe

---

### Post by 504harry on 2008-03-11
"sudo" - something like Super-User - it may be correctly defined elsewhere, but that's close enough.
Whilst it would be nice to be told this (rather than the meaningless comment you received from the PC)....but the program is written by folk that already know all this.

This "need to grant permission" is a great strength in Linux/Ubuntu - it prevents external hackers ( so I believe!) and naughty children ( and sometime us as well!)...from messing up the PC.
I don't understand enough to know why there aren't easy ways/hacks round this - but VERY grateful it works.
I've always used a dedicated HDD - so no dual-booting needed. However, it has its drawbacks (time rebooting mainly) and strength that I cannot screw-up two PC's at the same time. I found the Partitioninig confusing, but the installation (originally from a CD) and subsequent on-line up-dates is very clear. No, I should say "easy enough", for sadly I rarely use the Ubuntu PC except to write to the forum, get updates etc - - - in the hope someday I can transfer 100% - but computing is unlikley to be as easy as using a typewriter - and that's a great shame.

Good luck on your journey into Ubuntu.

---

