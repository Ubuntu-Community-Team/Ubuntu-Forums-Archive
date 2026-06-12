---
title: "I can never seem to $make - why?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by beesforbreath on 2006-07-22
Every time I try to
```
./configure
make
```
I'm told there's no makefile to be found. The last three I've tried, for example: mplayer, xine, and hydrogen - all official src releases from the websites. I unroll the tar file, cd to the directory, ./configure - which runs the checks and all is well - but then I get to make and it errors ("make: *** No targets specified and no makefile found.  Stop.") - when clearly in the folder there is a makefile. the xine release had two even (Makefile.am and Makefile.in).

am I missing some fundamental step between ./configure and $make?

---

### Post by Ziox on 2006-07-22
um...just out of curiosity, why are you making these files?
they can be easily installed from the ubuntu repositories...check my signature for installing and enabling extra repositories...

---

### Post by metaltailz on 2006-07-22
Do you have a source code compiler installed? With out that linux has no idea what the hell the command make means. Other than that I don't know what might be wrong.

---

### Post by Ziox on 2006-07-22
do you have build-essentials install, i think you need that to use make...

---

### Post by taurus on 2006-07-22
You need to look at either README or INSTALL to see exactly what you must do to build it!!!  Most of the time, it's ./configure && make && sudo make install but that's not always true...

---

### Post by lamego on 2006-07-22
To compile programs on Ubuntu you will need to install the build-essential package.
Searc for "build essential" on the package manager or install from the terminal using:
```
sudo apt-get install build-essential
```

---

### Post by beesforbreath on 2006-07-22
I have build-essential installed, and the reason I've been trying to compile these from source is that I've run into a bug with amaroK that may be resolved by compiling it myself (I was going to attempt the beta version). hydrogen and mplayer were only examples, the real issue is that I'm seriously lacking here in my inability to install from source.

oh, and the INSTALL/README files were generic install files instructing me to ```
./configure
make
```
all to no avail.

---

### Post by Iandefor on 2006-07-22
> **beesforbreath said:**
> I have build-essential installed, and the reason I've been trying to compile these from source is that I've run into a bug with amaroK that may be resolved by compiling it myself (I was going to attempt the beta version). hydrogen and mplayer were only examples, the real issue is that I'm seriously lacking here in my inability to install from source.

oh, and the INSTALL/README files were generic install files instructing me to ```
./configure
make
``` all to no avail. What is the output of ./configure?

---

### Post by taurus on 2006-07-22
And what is the output of 

```

ls -la

```

---

### Post by beesforbreath on 2006-07-22
amarok's ./configure:

beesforbreath@beesforbreath:/tmp/amarok-1.4.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking whether system headers can cope with -O2 -fno-inline... irrelevant
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
checking for PIE support... yes
checking if enabling -pie/fPIE support... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
beesforbreath@beesforbreath:/tmp/amarok-1.4.1$ make
make: *** No targets specified and no makefile found.  Stop.
beesforbreath@beesforbreath:/tmp/amarok-1.4.1$


(by the way, I very much appreciate the help thusfar)

---

### Post by beesforbreath on 2006-07-22
beesforbreath@beesforbreath:/tmp/amarok-1.4.1$ ls -la
total 2620
drwxr-xr-x  6 beesforbreath beesforbreath    4096 2006-07-22 12:57 .
drwxrwxrwt 18 root          root             4096 2006-07-22 12:57 ..
-rw-r--r--  1 beesforbreath beesforbreath  374902 2006-07-02 16:29 acinclude.m4
-rw-r--r--  1 beesforbreath beesforbreath  406096 2006-07-02 16:29 aclocal.m4
drwxr-xr-x  2 beesforbreath beesforbreath    4096 2006-07-02 15:37 admin
drwxr-xr-x  4 beesforbreath beesforbreath    4096 2006-07-02 16:29 amarok
-rw-r--r--  1 beesforbreath beesforbreath     491 2006-07-02 15:37 AUTHORS
-rw-r--r--  1 beesforbreath beesforbreath  119634 2006-07-02 15:37 ChangeLog
-rw-r--r--  1 beesforbreath beesforbreath    6910 2006-07-02 16:29 config.h.in
-rw-r--r--  1 beesforbreath beesforbreath   96623 2006-07-22 12:57 config.log
-rwxr-xr-x  1 beesforbreath beesforbreath 1235408 2006-07-02 16:29 configure
-rw-r--r--  1 beesforbreath beesforbreath     109 2006-07-02 16:29 configure.files
-rw-r--r--  1 beesforbreath beesforbreath   49843 2006-07-02 16:29 configure.in
-rw-r--r--  1 beesforbreath beesforbreath     178 2006-07-02 15:37 configure.in.bot
-rw-r--r--  1 beesforbreath beesforbreath     260 2006-07-02 15:37 configure.in.in
-rw-r--r--  1 beesforbreath beesforbreath   17995 2006-07-02 15:37 COPYING
drwxr-xr-x 14 beesforbreath beesforbreath    4096 2006-07-02 16:29 doc
-rw-r--r--  1 beesforbreath beesforbreath    7333 2006-07-02 15:37 INSTALL
-rwxr-xr-x  1 beesforbreath beesforbreath  202988 2006-07-22 12:57 libtool
-rw-r--r--  1 beesforbreath beesforbreath     102 2006-07-02 16:29 Makefile.am
-rw-r--r--  1 beesforbreath beesforbreath      80 2006-07-02 15:37 Makefile.am.in
-rw-r--r--  1 beesforbreath beesforbreath     450 2006-07-02 15:37 Makefile.cvs
-rw-r--r--  1 beesforbreath beesforbreath   31143 2006-07-02 16:30 Makefile.in
drwxr-xr-x 51 beesforbreath beesforbreath    4096 2006-07-02 16:29 po
-rw-r--r--  1 beesforbreath beesforbreath    7772 2006-07-02 15:37 README
-rw-r--r--  1 beesforbreath beesforbreath      14 2006-07-02 15:37 subdirs
-rw-r--r--  1 beesforbreath beesforbreath   16242 2006-07-02 15:37 TODO

---

### Post by taurus on 2006-07-22
From the ./configure's error message, you need to install X lib/dev package!!!  So, fire up synaptic and search for it...  And by the way, no need to go further with make if ./configure returns with an error message.

---

### Post by aysiu on 2006-07-22
As has been mentioned before, you don't need to compile these things from source (./configure make make install).

Read these two links to find out **the easy way** to install software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

In the meantime, for those particular packages, do this:

1. Get more repositories (more repositories mean more available software):
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Paste this one command into the terminal: ```
sudo aptitude update && sudo aptitude install xine mplayer amarok hydrogen
```

There. With that **one command** you've installed four programs.

---

### Post by lamego on 2006-07-22
If you are not familiar with compiling programs you will have some hard time to find the proper libraries:
The error you are getting now is because the program needs the X11 development files.
```
sudo apt-get install libx11-dev
```
Anyway, amarok is available from the ubuntu repos, you should use it instead unless you have a very strong reason to compile it yourself.

---

### Post by Iandefor on 2006-07-22
> **beesforbreath said:**
> amarok's ./configure:

beesforbreath@beesforbreath:/tmp/amarok-1.4.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking whether system headers can cope with -O2 -fno-inline... irrelevant
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
checking for PIE support... yes
checking if enabling -pie/fPIE support... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
beesforbreath@beesforbreath:/tmp/amarok-1.4.1$ make
make: *** No targets specified and no makefile found.  Stop.
beesforbreath@beesforbreath:/tmp/amarok-1.4.1$


(by the way, I very much appreciate the help thusfar) Well, there you go. You're missing a development library.

You need to install some development files, but I don't happen to know which ones. I shall return, hopefully with the knowledge of what you need!

EDIT: Looks like lamego found your package.

---

### Post by beesforbreath on 2006-07-22
Okay, so I feel a little silly, but I was missing kdebase-dev  - that seemed to fix what was ailing me. Thank you for the repositories I will certainly use them, but I should mention that this wasn't so much for amaroK/xine/hydrogen etc (I mean it was, I really do want to use them and will), but it's also me trying to educate myself on Linux, you know?

thanks so much guys.

---

### Post by aysiu on 2006-07-22
Part of that education is learning how to take advantage of the stability, ease of use, and comprehensiveness of the repositories.

There are basically four ways to install software in Ubuntu, and if you really want to educate yourself on Linux, you'll get to know all four ways.

Why start with the hardest way first?

---

### Post by taurus on 2006-07-22
> **aysiu said:**
> 
Why start with the hardest way first?
I guess that's what you call doing things the hard way!!!

---

### Post by Iandefor on 2006-07-22
> **aysiu said:**
> Part of that education is learning how to take advantage of the stability, ease of use, and comprehensiveness of the repositories.

There are basically four ways to install software in Ubuntu, and if you really want to educate yourself on Linux, you'll get to know all four ways.

Why start with the hardest way first? Four? I can only think of three:

[LIST=1]
[*]Package manager (apt)
[*]Precompiled binaries
[*]Compile from source[/LIST]
What am I missing?

---

### Post by aysiu on 2006-07-22
Well, I guess I split #2 into two separate ways--precompiled .deb files and precompiled .rpm files.

---

### Post by Iandefor on 2006-07-22
> **aysiu said:**
> Well, I guess I split #2 into two separate ways--precompiled .deb files and precompiled .rpm files. I see.
 
with #2 I was actually leaning towards something like the latest Blender, that's just a self-contained binary you can grab from the website and drop into /opt. Precompiled .debs/.rpms I think would fall under #1.

---

### Post by aysiu on 2006-07-22
So maybe there are five ways, then... or possibly six if you count auto-installers like Google Earth.

---

### Post by Iandefor on 2006-07-22
> **aysiu said:**
> So maybe there are five ways, then... or possibly six if you count auto-installers like Google Earth. There are auto-installers, and then you have stuff like autopackage and Klik. God, what a mess package management is on Linux :)!

1. package managers (repos)
2. package managers (non-repo ie, grabbed file from web)
3. precompiled downloadable binaries
4. compilable source code
5. automated installers
6. autopackage/klik

---

