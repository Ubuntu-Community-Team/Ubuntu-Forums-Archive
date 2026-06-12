---
title: "error while using command &quot;make&quot; and &quot;configure&quot;"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-22
i downloaded a program xvoice-0.9.6.tar.gz and i extracted it. I navigated my terminal to that path. i then typed ./configure and it says an error(see the first screenshot) and i typed "make" and it always(whenever i try to compile using this command) says an error [B]"make: *** No targets specified and no makefile found.  Stop.
[/B]

---

### Post by Lord Illidan on 2008-03-22
There is no screenshot attached.

I downloaded xvoice (very old program btw, 2004).
 and it seems that
If the ./configure script doesn't finish for some reason, then make will never work. ./configure is generating the makefile for you, thus since your ./configure didn't work, you got the error [B]make: *** No targets specified and no makefile found.  Stop.

[/B]Copy and paste the output of ./configure here, and we can help you further.

---

### Post by adi_das on 2008-03-22
The output is :
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/arvind/Desktop/xvoice-0.9.6/missing: Unknown `--run' option
Try `/home/arvind/Desktop/xvoice-0.9.6/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
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
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C++ preprocessor... g++ -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... no
checking if we can lock with hard links... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether -lc should be explicitly linked in... no
creating libtool
checking for X... no
checking for ANSI C header files... (cached) yes
checking If this system's ViaVoice was installed with Carlo Wood's vvinstall... no
checking for SmOpen in -lsmapi... no
configure: error: ViaVoice SMAPI runtime kit NOT found.

Make sure ViaVoice runtime is installed, or try setting --with-vv-libs=DIR.

---

### Post by fela on 2008-03-22
I'd do what it says, install whatever it needs. :D

---

### Post by jan quark on 2008-03-22
> IBM's ViaVoice Engine

xvoice is free software, but IBM's engine on which it depends is not. In order to run xvoice, you will need a licensed version of ViaVoice for Linux. (The xvoice development team is in the process of investigating open source speech recognition engines.)

To install xvoice from RPM, you only need the Run Time Kit (ViaVoice_runtime-3.x-x.x.rpm). IBM no longer provides this RPM for free download. The Runtime RPM is available as part of the IBM ViaVoice Dictation for Linux package, which can be purchased online for $39.95. IBM will only ship it within the U.S. and Canada. (There is a separate link to purchase in Canada.)

To build xvoice from source, you will need the ViaVoice Speech Recognition (ASR) SDK (ViaVoice-sdk-3.x-x.x.rpm). This RPM is no longer available from IBM.

If you need to build xvoice from source, or cannot get a copy of the Run Time Kit to install from RPM, please notify the mailing list; we will probably be able to help you. 

taken from the official site
[http://xvoice.sourceforge.net/](http://xvoice.sourceforge.net/)

so it seems you have to install this viavoice engine first

---

