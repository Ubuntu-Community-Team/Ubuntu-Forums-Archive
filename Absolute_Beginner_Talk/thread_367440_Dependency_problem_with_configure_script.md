---
title: "Dependency problem with configure script"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-02-22
I am a person who always has problems with installing and I encountered it again. I always have problems with dependencies because I don't know what to install and/or where to get those dependencies.

I ran the ./install script of BasKet Notepads expecting that it will do the job.

Along the way, this is what appeared...
```
   ========================================================================
  ((                    BasKet Note Pads Quick Installer                    ))
    ========================================================================


              Welcome to the BasKet Note Pads installer assistant.
             It will configure, build and install BasKet Note Pads.


                             What do you want to do?

  1/ Install BasKet Note Pads system wide (you will need the root password)
  2/ Install BasKet Note Pads in your user folder

Your choice (default is 1): 1








    ========================================================================
  ((                    BasKet Note Pads Quick Installer                    ))
    ========================================================================




      If you do not know what they are, you can ignore errors or warnings.

                      The process can take several minutes.
                  A beep will notify you when it will be done.
                              Press ENTER to start.











    ========================================================================
  ((                       Step 1 / 3 : Configuration                       ))
    ========================================================================


./configure --prefix=/usr
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as requested)
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

    ========================================================================
  ((                      An Error has Been Encountered                     ))
    ========================================================================


        In the most cases, some libraries are missing or cannot be found.
      Think to install the *-dev or *-devel packages of your distribution.
                     For example, if libmng cannot be found,
  please check if libmng AND libmng-devel packages are installed on your system.
      See the reported errors to know which librarie need to be installed.

```


I have libmng and libmng-devel installed. 

What could be the problem? 

What should I install? 

Is it really a dependency problem?

---

### Post by mykalreborn on 2007-02-22
did you do 
```
sudo aptitude install build-essential
```
and i think you have to install the kde base libraries. check synaptic and search for kde and look around. there should be a base package for kde.

---

### Post by wersdaluv on 2007-02-22
I have build-essential installed already.

When I typed the keywords "kde" and "base," I found out that kdebase-dev is not installed. I tried to install it using adept but it said that it break packages...
> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 

What can I do to satisfy dependencies this time?

---

### Post by mykalreborn on 2007-02-22
i have an idea, and i think it's going to work.
try to install amarok. you can do that from applications>add/remove programs. this will install kde base package because it won't work without it. 
this is crazy enough to work.:D
take care!

---

### Post by nickoli_02 on 2007-02-22
try this... 

```
sudo aptitude install kubuntu-desktop
```

This will install the KDE desktop environment and all KDE's libraries. You don't actually need to use KDE, but if you want you can select it as a session when you log in.

---

### Post by wersdaluv on 2007-02-22
The funny thing is that, I am already using amarok and Kubuntu since more than a month ago.

How could I survive without the kdebase-dev installed? Although I have kdebase, kdebase-bin, and kdebase-data installed

---

### Post by lamego on 2007-02-22
kdebase-dev is only required to build KDE apps, not to run them.

> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.
Make sure your repository list is correct.
Open a terminal and type:
```
sudo apt-get update
sudo apt-get install kdelibs4-dev
```

P.S.: Basket Note Pads is available on the repositories for easy installation, package "basket".

Also the latest version is available for (K)Ubuntu:
[http://basket.kde.org/downloads/?file=basket-1.0-kubuntu](http://basket.kde.org/downloads/?file=basket-1.0-kubuntu)

---

### Post by nickoli_02 on 2007-02-22
Oops my bad, kubuntu-desktop won't work, now, would it :popcorn:

---

### Post by wersdaluv on 2007-02-22
I'm so lucky to find this!--> [http://www.esnips.com/doc/1121e6f7-9...ket_1.0-1_i386](http://www.esnips.com/doc/1121e6f7-9...ket_1.0-1_i386)

I ran the .deb and it was installed. 

Why is that .debs do not require dependencies?

---

### Post by mykalreborn on 2007-02-23
> Why is that .debs do not require dependencies?
they do require. you just stumbled on one that had the dependencies inside the package. most .debs actually require dependencies to be installed separately.
but there is autopackage or module packages (if you are on a slackware linux) that have the dependencies built right in.

---

