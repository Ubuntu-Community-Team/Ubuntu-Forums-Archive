---
title: "kxdocker ./configure error"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by limac on 2007-11-07
hi,

after downloading the .tar.bz2 of kxdocker 1.1.4a. And then after untarring it when i tried compiling it, after I entered the command ./configure, it com up with this with the error a the end:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
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
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
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
checking for egrep... grep -E
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
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
checking if g++ supports -c -o file.o... yes
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
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
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
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
limac@limac-laptop:~/Desktop/kxdocker-1.1.4a$ 

So what is wrong with this? Are there any dependencies that I need to install??

Thnx

---

### Post by Paul820 on 2007-11-07
You need the Qt headers that are greater than or equal to 3.2 but less than version 4.0 You need to look in synaptic for libqt3-headers.

---

### Post by llamakc on 2007-11-07
Yes. See your earlier thread where you asked a similar question and were answered. 

What do you think you need to install? Seriously. It is time for you to start learning. What from that error do you think needs to be installed? 

I want to help you learn so you stop flooding the forums with the same question again and again.

---

### Post by limac on 2007-11-07
that's all I need??

---

### Post by limac on 2007-11-07
yo srry llamack. that was my cousin who asked that question while i went for dinner. srry anyway.

---

### Post by Maestro23 on 2007-11-07
> **limac said:**
> that's all I need??

Here's your 4-page thread on the very same problem.

[http://ubuntuforums.org/showthread.php?t=596698](http://ubuntuforums.org/showthread.php?t=596698)

---

### Post by Paul820 on 2007-11-07
Yes, at the end of every unsuccessful configure there will be an error indicating what is required to make the program. In your case the error is:
> checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!

Configure checks that every file or header file is present before allowing you to continue with a make and make instal, otherwise make will just fail.

---

### Post by llamakc on 2007-11-07
> **limac said:**
> yo srry llamack. that was my cousin who asked that question while i went for dinner. srry anyway.

I'm going to unsubscribe from this and not follow any more of your posts. I find it unlikely that two people have the same posting style and verbiage.

Good luck limac. I recommend you embrace Ubuntu and GNU/Linux for what it is, and not what it is not.

There is no way you have read and studied all of the pages I have linked in for you. Later.

---

### Post by Paul820 on 2007-11-07
If the source has been packaged well there should be a text file in there called 'INSTALL', usually inside that it will tell you what it's dependencies are.

---

### Post by limac on 2007-11-07
what do u mean "unsubscribe"?

---

### Post by Paul820 on 2007-11-07
S/he was subscribed to the thread so any new post s/he will get notified.

---

### Post by llamakc on 2007-11-07
I'm not going to pay attention to your issues anymore because you continually ask the same questions over and over, and these questions have been answered over and over.

---

### Post by limac on 2007-11-07
why would u like to unsubscribe, llamack?

---

### Post by limac on 2007-11-07
> **llamakc said:**
> I'm not going to pay attention to your issues anymore because you continually ask the same questions over and over, and these questions have been answered over and over.

Well for my previous set the error was something different and for this it's showing something else...

---

### Post by limac on 2007-11-08
now after satisfying all the dependencies it is saying "cannot find -lXtst" and then a bunch of "ERROR"s written. 

How can i get rid of this issue??

Thnx

---

