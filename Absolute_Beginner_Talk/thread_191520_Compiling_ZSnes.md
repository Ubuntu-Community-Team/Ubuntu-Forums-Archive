---
title: "Compiling ZSnes"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by camRW on 2006-06-07
I tried to compile ZSnes and I get this error:

cam@ubuntu:~/Desktop/zsnes_1_42/src$ sudo ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for a BSD-compatible install... /usr/bin/install -c
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.1.0... yes
checking for libpng - version >= 1.2.0... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking for glGetError in -lGL... yes
checking for OpenGL... yes
checking if you want gdb friendly executable... no
checking which processor class to optimize for... 686
checking for egrep... grep -E
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
checking whether sys/types.h defines makedev... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged


ZSNES v1.41

SDL support                         Version 1.2.9
NASM support                        NASM version 0.98.38 compiled on Jun 27 2005ZLib support                        Version 1.2.3
PNG support (png screenshots)       Yes, version 1.2.8
OpenGL support                      Yes

The binary will be installed in /usr/local/bin

Configure complete, now type 'make' and pray.

cam@ubuntu:~/Desktop/zsnes_1_42/src$ make
gcc  -pipe -I. -Wall -I/usr/local/include -I/usr/include -D__LINUX__  -I/usr/include/SDL -D_REENTRANT  -D__OPENGL__ -O3 -ffast-math -fomit-frame-pointer -fexpensive-optimizations -s -march=pentiumpro -o chips/dsp1emu.o -c chips/dsp1emu.c
In file included from chips/dsp1emu.c:27:
chips/../gblhdr.h:85:20: error: GL/gl.h: No such file or directory
make: *** [chips/dsp1emu.o] Error 1


I tried sudo make and sudo make install as well.  Anyone know what the problem is?

And yes, I know that you can get ZSnes from the repositories.

---

### Post by Monarchos on 2006-06-07
Heya,  Long time PC User, first time penguin.  I'm learning Linux more and more everyday, where do you get ZSnes and Roms?

---

### Post by %hMa@?b&lt;C on 2006-06-07
instead of compiling from source, why not grab zsnes from the repos?
```
sudo apt-get install zsnes
```
type that from the command line.

Also Saying where to find roms is borderline illeagle, but google is your friend there.

---

### Post by camRW on 2006-06-07
I may not have made myself clear in my message, but I'm trying to learn more about installing without using the repositories.  I've seen the "How to install anything in Ubuntu page" and I'm trying to build off of that.

---

