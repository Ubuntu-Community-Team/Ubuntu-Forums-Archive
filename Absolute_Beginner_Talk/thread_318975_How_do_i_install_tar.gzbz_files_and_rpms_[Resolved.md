---
title: "How do i install tar.gz/bz files and rpms [Resolved]"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by synt4xerr0r on 2006-12-14
How do i install them for example
if i have lets say... gambas2-1.9.46a.tar.bz2

---

### Post by taurus on 2006-12-14
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by jpeddicord on 2006-12-14
.tar.bz2 files are lile .zip files. Just click on them to open them, then click the Extract button. It will extract all of the files to a folder from where you can run the application. If you can't find any "runnable" files when you extract it, then you will have to open a terminal and run these commands: **./configure**, **make**, **sudo make install**. It should compile itself and then install on the last command.

As for .rpm's, don't try to install them. It's more of a pain to use them than it is to just find equivalent .deb files. What .rpm do you want to install? I'm sure you can find a .deb for it.

Jacob

---

### Post by synt4xerr0r on 2006-12-14
argh what am i doing wrong install is failing
```

syntaxerr0r@SyntaxError:~/Desktop$ cd /home/syntaxerr0r/Desktop/gambas2-1.9.46
syntaxerr0r@SyntaxError:~/Desktop/gambas2-1.9.46$ ./configure
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
configure: configuring in main
configure: running /bin/sh './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... i686-pc-linux-gnu
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for setenv... yes
checking for unsetenv... yes
checking for getdomainname... yes
checking for getpt... yes
checking for ccache... no
checking for main in -lm... yes
checking for main in -lz... yes
checking for main in -lgcc_s... yes
checking for main in -lstdc++... no
checking target system... LINUX
checking which extension is used for shared libraries... .so
checking for threading compiler options... -D_REENTRANT
checking for threading linker options... -lpthread
checking for mathematic libraries... -lm
checking CFLAGS for gcc -fvisibility=hidden... -fvisibility=hidden
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
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
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
configure: error: /bin/sh './configure' failed for main

```

---

### Post by jpeddicord on 2006-12-14
Aha! You need to install the build-essential package:
```
sudo apt-get install build-essential
```
Then try the three steps again. :)

---

### Post by synt4xerr0r on 2006-12-14
> **jacobmp92 said:**
> Aha! You need to install the build-essential package:
```
sudo apt-get install build-essential
```
Then try the three steps again. :)

Thankyou soooo much! worx now and i will use knowledge learned from this thread to install other files

---

### Post by civic_si on 2006-12-14
try installing Alien to convert the RPM files to Deb Files

sudo apt-get install alien

the command to turn the RPM to a DEB is

sudo alien -d name-of-RPM.RPM

that will turn it into a deb file actually i think you can leave the -d out but it is habit for me to do it.

You can turn some tar.bz2 files into deb with this also. See if this works for you.

you can install .DEB files 

sudo dpkg -i name-of-package.deb

---

### Post by Synt4x_3rr0r on 2006-12-14
> **synt4xerr0r said:**
> Thankyou soooo much! worx now and i will use knowledge learned from this thread to install other files

Just remember to first look for a ubuntu package. There usually is one ready to just install, no need to compile yourself.
But if there is no ubuntu package or if the ubuntu package isnt the latest version and you need that, you can compile it yourself.

But compiling can be kind of hard depending on what you want to compile.

---

### Post by synt4xerr0r on 2006-12-14
> **Synt4x_3rr0r said:**
> Just remember to first look for a ubuntu package. There usually is one ready to just install, no need to compile yourself.
But if there is no ubuntu package or if the ubuntu package isnt the latest version and you need that, you can compile it yourself.

But compiling can be kind of hard depending on what you want to compile.

nice name

---

### Post by Synt4x_3rr0r on 2006-12-14
> **synt4xerr0r said:**
> nice name

Haha i first thought I had quoted myself :D

---

### Post by civic_si on 2006-12-14
thats funny   :)

---

### Post by synt4xerr0r on 2006-12-14
> **Synt4x_3rr0r said:**
> Haha i first thought I had quoted myself :D

lol  :D 

we should hang out more :-k

---

### Post by tchoklat on 2006-12-27
trying to istall kofice from tar.bz2 file manually. I follow tyhe guidelines here, thouigh when I enter "make" I get :

tony@tony:~$ cd /home/tony/Desktop/koffice-1.6.1
tony@tony:~/Desktop/koffice-1.6.1$ ./configure
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
checking for gcc option to accept ISO C89... none needed
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
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
tony@tony:~/Desktop/koffice-1.6.1$ make
make: *** No targets specified and no makefile found.  Stop.


Tony

---

### Post by taurus on 2006-12-27
You probably need the xorg-dev package (and no need to run **make** if ./configure returns with an error message...).

```
sudo aptitude update
sudo aptitude install xorg-dev
```

---

### Post by tchoklat on 2006-12-27
I will try that thanks

---

### Post by tchoklat on 2006-12-27
......

checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
tony@tony:~/Desktop/koffice-1.6.1$ make
make: *** No targets specified and no makefile found.  Stop.
tony@tony:~/Desktop/koffice-1.6.1$

---

### Post by taurus on 2006-12-27
You now need to install the -dev for qt.  I think it's called qt-dev or qt3-dev (or even qt4-dev)!!!

Try to see if there is qt-dev from a terminal then!

```
sudo aptitude install qt-dev
```

---

### Post by tchoklat on 2006-12-27
not having much luck here

no package called qt-dev, or qt2.dev etc

---

### Post by taurus on 2006-12-27
Go into System -> Administrator and click on Synaptic.  Than in the Search field, type **qt** and look for the one that end with **-dev** (starts with qt or libqt).  That's what you need to build koffice...
  
By the way, do you know that there is a binary for kubuntu that you can install with synaptic/apt-get/aptitude???

[http://kubuntu.org/announcements/koffice-161.php](http://kubuntu.org/announcements/koffice-161.php)

---

### Post by tchoklat on 2006-12-27
no I didn't - I will use that instead.

thanks friend!

---

### Post by taurus on 2006-12-27
It's much easier just to add a repo to /etc/apt/sources.list and apt-get it that way...

---

### Post by ashmew2 on 2006-12-28
So Many Syntax Errors on Ubuntu Forums :P

---

