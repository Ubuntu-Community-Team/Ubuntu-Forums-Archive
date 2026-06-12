---
title: "compile error"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by rocketboyjro on 2007-03-23
Hi, I'm trying to install a program but whenever I ./configure it spits this out at me.

```
jason@jason-desktop:~/Desktop/kcddaemon$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

Sorry for the n00b question, still getting the hang of linux 
Thanks

---

### Post by yabbadabbadont on 2007-03-23
Try installing kde-devel and see if it helps.

```
/home/bubba $ aptitude show kde-devel
Package: kde-devel
State: not installed
Version: 5:47
Priority: extra
Section: universe/kde
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Uncompressed Size: 41.0k
Depends: kde-core (>= 5:47), kdesdk (>= 4:3.4.3), libartsc0-dev (>= 1.4.2), libarts1-dev (>= 1.4.2), kdelibs4-dev (>=
         4:3.4.3), kdebase-dev (>= 4:3.4.3), libkonq4-dev (>= 4:3.4.3), qt3-designer
Suggests: kde-i18n (>= 4:3.4.3)
Description: the K Desktop Environment development files and modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical desktop environment for Unix workstations. It combines
 ease of use, contemporary functionality, and outstanding graphical design with the technological superiority of the Unix
 operating system. 
 
 This metapackage includes official KDE modules that are useful to developers, including KDE's software development kit
 (SDK), Qt3's designer tool, and all core KDE header and development packages.

```

---

### Post by zvacet on 2007-03-23
```
sudo aptitude install build-essential
```

---

### Post by yabbadabbadont on 2007-03-23
> **zvacet said:**
> ```
sudo aptitude install build-essential
```

Look at the top of his ./configure output...  I would bet that he already has it or the first few tests would have failed.  ;)

---

### Post by rocketboyjro on 2007-03-23
> **yabbadabbadont said:**
> Try installing kde-devel and see if it helps.


is there any way to install all of the dependencies that kde-devel needs?

besides going one by one

---

### Post by tonyr1988 on 2007-03-23
> **rocketboyjro said:**
> is there any way to install all of the dependencies that kde-devel needs?

besides going one by one
If you:

> sudo apt-get install kde-devel

It should install / configure all the dependencies for you (isn't apt great?) :)

---

### Post by Bachstelze on 2007-03-23
Maybe he just doesn't have an Internet connection. In that case, it will be far more complicated and, to be honest, I think it would be better to just ditch Ubuntu and replace it with e.g. Debian.

---

### Post by rocketboyjro on 2007-03-23
> **tonyr1988 said:**
> If you:

Quote:
sudo apt-get install kde-devel

It should install / configure all the dependencies for you (isn't apt great?) 

I'm retarded, I keep forgetting to put sudo in front of apt-get, thanks!

---

### Post by dfreer on 2007-03-23
> I think it would be better to just ditch Ubuntu and replace it with e.g. Debian.
Forgive me if I am wrong, but doesn't Debian handle dependencies that same way? using apt-get? Come to think of it, is there any distro that treats programs like windows does, that is putting everything it needs in the .exe? That way you could download your package from let's say the universities T1 line, bring it home and not worry about dependencies (or very few). 

Lol as for the OP, could it be something in his configure script? perhaps the program can be compiled for gnome instead of KDE?

---

### Post by rocketboyjro on 2007-03-23
I should have said this in the first post but I'm running Edgy, if that makes a difference.

> **HymnToLife said:**
> Maybe he just doesn't have an Internet connection. In that case, it will be far more complicated and, to be honest, I think it would be better to just ditch Ubuntu and replace it with e.g. Debian.

I've got an Internet connection but after I did 

```
sudo apt-get install kde-devel
```

it gave me this

```
jason@jason-desktop:~/Desktop/kcddaemon$ sudo apt-get install kde-devel
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde-devel: Depends: kdesdk (>= 4:3.4.3) but it is not going to be installed
             Depends: kdelibs4-dev (>= 4:3.4.3) but it is not going to be installed
             Depends: kdebase-dev (>= 4:3.4.3) but it is not going to be installed
             Depends: libkonq4-dev (>= 4:3.4.3) but it is not going to be installed
E: Broken packages

```

and i've already tried to

```
sudo apt-get -f install
```

I'm about to give up on this program.

---

### Post by NoUseForANick on 2007-04-04
Hi,

try with

./configure --prefix=/usr

if you already have the kde headers installed.

Good luck!

---

### Post by apostlenaresh on 2007-04-17
hi there 

    i am doing my assignment for my Network Security Subject. I am problem compiling .. keep hitting this message after trying everything that is aforesaid step above. Please assist me thank u . 

 
 apostlenaresh@apostlenaresh:~/Desktop/naresh$  ./configure
loading cache ./config.cache
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
***checking whether the C compiler (gcc  ) is a cross-compiler... no***
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking whether make sets ${MAKE}... (cached) yes
configuring for
checking for pow in -lm... (cached) yes
checking for OpenSSL include files... found in /usr/include
checking for OpenSSL libraries... found in /usr/lib
checking how to run the C preprocessor... (cached) gcc -E
checking for ANSI C header files... (cached) yes
checking for 8-bit clean memcmp... (cached) yes
checking return type of signal handlers... (cached) void
checking for vprintf... (cached) yes
checking for strdup... (cached) yes
creating ./config.status
creating Makefile


 except for the one in Bold and italic .. i believe rest is all ok . PLEASE ASSIST ME ASAP .. thank u ,,, 
 sincerely NARESH

---

