---
title: "[SOLVED] Error Compiling Game"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-20
Hi I found this game on kde-look.org and wanted to try it out. Here is the link:
[http://www.kde-apps.org/content/show.php/kbilliards?content=17723](http://www.kde-apps.org/content/show.php/kbilliards?content=17723)

They didnt have a binary for kubuntu so I downloaded the source and I tried to install it. I used auto-apt so that I could use checkinstall instead of make install. Here what I got:

sudarshan@Lucky-Linux:~/Games/kbilliards-0.8.7b$ auto-apt run ./configure
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
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
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

I tried to search for the missing header files (crt_externs.h etc) using auto-apt serach..but nothing happened. One more thing is that the last line about X, that error came when I tried to install Gazebo (a robot simulation software i need for my research). So does this error have anything to do with my display?

Thanks.

---

### Post by Bachstelze on 2007-06-20
```
sudo apt-get install xorg-dev
```

---

### Post by linuxnovice on 2007-06-20
I am installing that now. Could you please tell what error it was and what is xorg-dev? And I would like to know whether ./configure actually installs anyting on my system or not. I am under the impression that ./configure just makes the stuff ready to be installed...

Thanks.

---

### Post by Bachstelze on 2007-06-20
> **linuxnovice said:**
> 
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!


Your X implementation is Xorg, you need the development files for it, thus *xorg-dev* :)

---

### Post by atria on 2007-06-20
xorg-dev contains the development files for xorg and its relevant components.

The game you are trying to compile requires those include files for the xorg functions which are required for the compilation.

configure is a script that checks whether the required dependencies are found so that compilation can proceed correctly.

Hope that helps

---

### Post by linuxnovice on 2007-06-20
After I installed xorg-dev I tried the game install agian. I got an error again. Here is the stuff:

sudarshan@Lucky-Linux:~/Games/kbilliards-0.8.7b$ auto-apt run ./configure
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
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
checking for libpng... no
checking for libjpeg6b... no
checking for libjpeg... no
configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

---

### Post by linuxnovice on 2007-06-20
I cant seem to include the config.log. If I copy the contents it says its too long. If I try to attach it , it says invalid file upload error.

---

### Post by atria on 2007-06-20
Enter this into the terminal:
```
sudo aptitude install libqt4-dev libqt4-core
```

---

### Post by Seisen on 2007-06-20
You need to install Qt, ah the joys of trying to compile a program.

---

### Post by Bachstelze on 2007-06-20
Don't think Qt4 would work

```
sudo apt-get install libqt3-mt-dev
```

---

### Post by linuxnovice on 2007-06-20
Indeed. I figured I need to install Qt. However, I dont know how to install Qt. Can someone help on that?

---

### Post by atria on 2007-06-20
Include the core libraries for qt3 too so it becomes
```

sudo apt-get install libqt3-mt-dev libqt3-mt
```

//edit
[quote=linuxnovice]However, I dont know how to install Qt. Can someone help on that? [/quote]

We just posted the solutions?

---

### Post by linuxnovice on 2007-06-20
Hi, 

I installed Qt4 it didnt work. Then I installed Qt3 it worked but stopped at another error. Here are the details:

sudarshan@Lucky-Linux:~/Games/kbilliards-0.8.7b$ auto-apt run ./configure
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
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
checking whether g++ supports -Wl,--allow-shlib-undefined... ^[1yes
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
checking the maximum length of command line arguments... 132768
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

So what next?

By the way what is Qt? I just like to know so that the next i encounter i wouldnt be totally clueless. Since Qt4 is not working and i have no use for it, how do I uninstall it?

Thanks.

---

### Post by atria on 2007-06-20
Dependency hell FTL

Weird qt4 didnt work for you, anyway heres the command to remove it
```
sudo aptitude purge libqt4-dev libqt4-core
```

Qt is a framework for the fanciful windows you see in kde.

Anyway to fix the new error, use this:
```
sudo aptitude install kde-devel
```

If you get a similar error message again, do a
```
aptitude search <packagename>
```
and install the development package (those that end with a -dev)

[edit]
If kde-devel fetches too many packages, you might want to try kdebase-dev instead and see if it works.
[/edit]

---

### Post by linuxnovice on 2007-06-20
Thanks fellows, 

I installed the kdebase-dev because kde-devel told me it had to download 40mb of stuff and would take up 140mb of harddisk space. So I installed it and configure worked and it told me to go on to make.

So I did a make and got the following:

sudarshan@Lucky-Linux:~/Games/kbilliards-0.8.7b$ sudo make
Password:
cd . && make -f admin/Makefile.common configure.in ;
make  all-recursive
make[1]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b'
cd . && make -f admin/Makefile.common configure.in ;
Making all in doc
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
Making all in media
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
Making all in sound
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/sound'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/sound'
Making all in balls
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/balls'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/balls'
Making all in other
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/other'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/other'
Making all in maps
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/maps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/maps'
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
Making all in po
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/po'
Making all in src
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/src'
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -o confdialog.h ./confdialog.ui
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -o dlgscoresui.h ./dlgscoresui.ui
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -o initgamewindowui.h ./initgamewindowui.ui
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
In file included from main.cpp:22:
kbilliards.h:31:19: error: qlist.h: No such file or directory
/usr/include/kde/arts/notification.h:54: warning: &#8216;class Arts::NotificationClient&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/iomanager.h:93: warning: &#8216;class Arts::IONotify&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/iomanager.h:112: warning: &#8216;class Arts::TimeNotify&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/startupmanager.h:42: warning: &#8216;class Arts::StartupClass&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/factory.h:45: warning: &#8216;class Arts::Factory&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/idlfilereg.h:41: warning: &#8216;class Arts::IDLFileReg&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/datapacket.h:43: warning: &#8216;class Arts::GenericDataChannel&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/asyncstream.h:44: warning: &#8216;class Arts::GenericAsyncStream&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/asyncstream.h: In instantiation of &#8216;Arts::AsyncStream<float>&#8217;:
/usr/include/kde/arts/asyncstream.h:88:   instantiated from here
/usr/include/kde/arts/asyncstream.h:63: warning: &#8216;class Arts::AsyncStream<float>&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/asyncstream.h:88: warning: &#8216;class Arts::FloatAsyncStream&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/asyncstream.h: In instantiation of &#8216;Arts::AsyncStream<unsigned char>&#8217;:
/usr/include/kde/arts/asyncstream.h:95:   instantiated from here
/usr/include/kde/arts/asyncstream.h:63: warning: &#8216;class Arts::AsyncStream<unsigned char>&#8217; has virtual functions but non-virtual destructor
/usr/include/kde/arts/asyncstream.h:95: warning: &#8216;class Arts::ByteAsyncStream&#8217; has virtual functions but non-virtual destructor
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b'
make: *** [all] Error 2

I thought all the dependency checks only came duing the configuration stage..and it should be a breeze after that? Any suggestions?

---

### Post by Bachstelze on 2007-06-20
Install *libqt3-compat-headers*. Also, you don't need to *sudo make*, just *make* will do :

```
sudo apt-get install libqt3-compat-headers
sudo make clean
make
```

---

### Post by linuxnovice on 2007-06-20
I did what you told me and make worked. Then I did a checkinstall and it seems to have installed the stuff.

Here is the details:
sudarshan@Lucky-Linux:~/Games/kbilliards-0.8.7b$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Checkinstall Docs
>>

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@Lucky-Linux ]
1 -  Summary: [ Checkinstall Docs ]
2 -  Name:    [ kbilliards ]
3 -  Version: [ 0.8.7b ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ kbilliards-0.8.7b ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
cd . && make -f admin/Makefile.common configure.in ;
Making install in doc
make[1]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
make[1]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/doc'
Making install in media
make[1]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
Making install in sound
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/sound'
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/sound'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/sound/
mkdir -p -- /usr/local/kde/share/apps/kbilliards/sound/
/usr/bin/install -c -p -m 644 ./ballinhole.wav /usr/local/kde/share/apps/kbilliards/sound/ballinhole.wav
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/sound/ballinhole.wav': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/sound/
/usr/bin/install -c -p -m 644 ./hitball.wav /usr/local/kde/share/apps/kbilliards/sound/hitball.wav
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/sound/hitball.wav': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/sound/
/usr/bin/install -c -p -m 644 ./hitedge.wav /usr/local/kde/share/apps/kbilliards/sound/hitedge.wav
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/sound/hitedge.wav': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/sound/
/usr/bin/install -c -p -m 644 ./gameover.wav /usr/local/kde/share/apps/kbilliards/sound/gameover.wav
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/sound/gameover.wav': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/sound/
/usr/bin/install -c -p -m 644 ./music01.ogg /usr/local/kde/share/apps/kbilliards/sound/music01.ogg
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/sound/music01.ogg': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/sound/
/usr/bin/install -c -p -m 644 ./applause.wav /usr/local/kde/share/apps/kbilliards/sound/applause.wav
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/sound/applause.wav': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/sound/
/usr/bin/install -c -p -m 644 ./shot.wav /usr/local/kde/share/apps/kbilliards/sound/shot.wav
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/sound/shot.wav': No such file or directory
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/sound'
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/sound'
Making install in balls
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/balls'
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/balls'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
mkdir -p -- /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball01.png /usr/local/kde/share/apps/kbilliards/balls/ball01.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball01.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball02.png /usr/local/kde/share/apps/kbilliards/balls/ball02.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball02.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball03.png /usr/local/kde/share/apps/kbilliards/balls/ball03.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball03.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball04.png /usr/local/kde/share/apps/kbilliards/balls/ball04.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball04.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball05.png /usr/local/kde/share/apps/kbilliards/balls/ball05.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball05.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball06.png /usr/local/kde/share/apps/kbilliards/balls/ball06.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball06.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball07.png /usr/local/kde/share/apps/kbilliards/balls/ball07.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball07.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball08.png /usr/local/kde/share/apps/kbilliards/balls/ball08.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball08.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball09.png /usr/local/kde/share/apps/kbilliards/balls/ball09.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball09.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball10.png /usr/local/kde/share/apps/kbilliards/balls/ball10.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball10.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball11.png /usr/local/kde/share/apps/kbilliards/balls/ball11.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball11.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball12.png /usr/local/kde/share/apps/kbilliards/balls/ball12.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball12.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball13.png /usr/local/kde/share/apps/kbilliards/balls/ball13.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball13.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball14.png /usr/local/kde/share/apps/kbilliards/balls/ball14.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball14.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball15.png /usr/local/kde/share/apps/kbilliards/balls/ball15.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball15.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./whiteball.png /usr/local/kde/share/apps/kbilliards/balls/whiteball.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/whiteball.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball01b.png /usr/local/kde/share/apps/kbilliards/balls/ball01b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball01b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball02b.png /usr/local/kde/share/apps/kbilliards/balls/ball02b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball02b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball03b.png /usr/local/kde/share/apps/kbilliards/balls/ball03b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball03b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball04b.png /usr/local/kde/share/apps/kbilliards/balls/ball04b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball04b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball05b.png /usr/local/kde/share/apps/kbilliards/balls/ball05b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball05b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball06b.png /usr/local/kde/share/apps/kbilliards/balls/ball06b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball06b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball07b.png /usr/local/kde/share/apps/kbilliards/balls/ball07b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball07b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball08b.png /usr/local/kde/share/apps/kbilliards/balls/ball08b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball08b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball09b.png /usr/local/kde/share/apps/kbilliards/balls/ball09b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball09b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball10b.png /usr/local/kde/share/apps/kbilliards/balls/ball10b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball10b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball11b.png /usr/local/kde/share/apps/kbilliards/balls/ball11b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball11b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball12b.png /usr/local/kde/share/apps/kbilliards/balls/ball12b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball12b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball13b.png /usr/local/kde/share/apps/kbilliards/balls/ball13b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball13b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball14b.png /usr/local/kde/share/apps/kbilliards/balls/ball14b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball14b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball15b.png /usr/local/kde/share/apps/kbilliards/balls/ball15b.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball15b.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball_shadow.png /usr/local/kde/share/apps/kbilliards/balls/ball_shadow.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball_shadow.png': No such file or directory
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/balls/
/usr/bin/install -c -p -m 644 ./ball_shadowb.png /usr/local/kde/share/apps/kbilliards/balls/ball_shadowb.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/balls/ball_shadowb.png': No such file or directory
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/balls'
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/balls'
Making install in other
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/other'
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/other'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/
/usr/bin/install -c -p -m 644 ./*.png /usr/local/kde/share/apps/kbilliards/
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/ball.png': No such file or directory
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/leftarrow.png': No such file or directory
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/numbers.png': No such file or directory
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/rightarrow.png': No such file or directory
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/other'
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/other'
Making install in maps
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/maps'
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/maps'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/local/kde/share/apps/kbilliards/maps/
mkdir -p -- /usr/local/kde/share/apps/kbilliards/maps/
/usr/bin/install -c -p -m 644 ./kbilliards2004.kbm /usr/local/kde/share/apps/kbilliards/maps/kbilliards2004.kbm
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/maps/kbilliards2004.kbm': No such file or directory
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/maps'
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media/maps'
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
make[3]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
make[1]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/media'
Making install in po
make[1]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/po'
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/po'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/po'
make[1]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/po'
Making install in src
make[1]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/src'
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b/src'
test -z "/usr/local/kde/bin" || mkdir -p -- "/usr/local/kde/bin"
  /bin/bash ../libtool --silent --mode=install /usr/bin/install -c -p  'kbilliards' '/usr/local/kde/bin/kbilliards'
/usr/bin/install: setting permissions for `/usr/local/kde/bin/kbilliards': No such file or directory
/bin/bash ../admin/mkinstalldirs /usr/local/kde/share/icons/locolor/16x16/apps
mkdir -p -- /usr/local/kde/share/icons/locolor/16x16/apps
/usr/bin/install -c -p -m 644 ./lo16-app-kbilliards.png /usr/local/kde/share/icons/locolor/16x16/apps/kbilliards.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/icons/locolor/16x16/apps/kbilliards.png': No such file or directory
/bin/bash ../admin/mkinstalldirs /usr/local/kde/share/icons/hicolor/48x48/apps
mkdir -p -- /usr/local/kde/share/icons/hicolor/48x48/apps
/usr/bin/install -c -p -m 644 ./hi48-app-kbilliards.png /usr/local/kde/share/icons/hicolor/48x48/apps/kbilliards.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/icons/hicolor/48x48/apps/kbilliards.png': No such file or directory
/bin/bash ../admin/mkinstalldirs /usr/local/kde/share/icons/locolor/32x32/apps
mkdir -p -- /usr/local/kde/share/icons/locolor/32x32/apps
/usr/bin/install -c -p -m 644 ./lo32-app-kbilliards.png /usr/local/kde/share/icons/locolor/32x32/apps/kbilliards.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/icons/locolor/32x32/apps/kbilliards.png': No such file or directory
/bin/bash ../admin/mkinstalldirs /usr/local/kde/share/icons/hicolor/16x16/apps
mkdir -p -- /usr/local/kde/share/icons/hicolor/16x16/apps
/usr/bin/install -c -p -m 644 ./hi16-app-kbilliards.png /usr/local/kde/share/icons/hicolor/16x16/apps/kbilliards.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/icons/hicolor/16x16/apps/kbilliards.png': No such file or directory
/bin/bash ../admin/mkinstalldirs /usr/local/kde/share/icons/hicolor/32x32/apps
mkdir -p -- /usr/local/kde/share/icons/hicolor/32x32/apps
/usr/bin/install -c -p -m 644 ./hi32-app-kbilliards.png /usr/local/kde/share/icons/hicolor/32x32/apps/kbilliards.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/icons/hicolor/32x32/apps/kbilliards.png': No such file or directory
/bin/bash ../admin/mkinstalldirs /usr/local/kde/share/icons/hicolor/22x22/apps
mkdir -p -- /usr/local/kde/share/icons/hicolor/22x22/apps
/usr/bin/install -c -p -m 644 ./hi22-app-kbilliards.png /usr/local/kde/share/icons/hicolor/22x22/apps/kbilliards.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/icons/hicolor/22x22/apps/kbilliards.png': No such file or directory
/bin/bash ../admin/mkinstalldirs /usr/local/kde/share/icons/hicolor/64x64/apps
mkdir -p -- /usr/local/kde/share/icons/hicolor/64x64/apps
/usr/bin/install -c -p -m 644 ./hi64-app-kbilliards.png /usr/local/kde/share/icons/hicolor/64x64/apps/kbilliards.png
/usr/bin/install: setting permissions for `/usr/local/kde/share/icons/hicolor/64x64/apps/kbilliards.png': No such file or directory
/bin/bash ../admin/mkinstalldirs /usr/local/kde/share/icons/hicolor/scalable/apps
mkdir -p -- /usr/local/kde/share/icons/hicolor/scalable/apps
/usr/bin/install -c -p -m 644 ./hisc-app-kbilliards.svgz /usr/local/kde/share/icons/hicolor/scalable/apps/kbilliards.svgz
/usr/bin/install: setting permissions for `/usr/local/kde/share/icons/hicolor/scalable/apps/kbilliards.svgz': No such file or directory
test -z "/usr/local/kde/share/applnk/Games" || mkdir -p -- "/usr/local/kde/share/applnk/Games"
 /usr/bin/install -c -p -m 644 'kbilliards.desktop' '/usr/local/kde/share/applnk/Games/kbilliards.desktop'
/usr/bin/install: setting permissions for `/usr/local/kde/share/applnk/Games/kbilliards.desktop': No such file or directory
test -z "/usr/local/kde/share/apps/kbilliards" || mkdir -p -- "/usr/local/kde/share/apps/kbilliards"
 /usr/bin/install -c -p -m 644 'kbilliardsui.rc' '/usr/local/kde/share/apps/kbilliards/kbilliardsui.rc'
/usr/bin/install: setting permissions for `/usr/local/kde/share/apps/kbilliards/kbilliardsui.rc': No such file or directory
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/src'
make[1]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b/src'
make[1]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b'
cd . && make -f admin/Makefile.common configure.in ;
make[2]: Entering directory `/home/sudarshan/Games/kbilliards-0.8.7b'
cd . && make -f admin/Makefile.common configure.in ;
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b'
make[1]: Leaving directory `/home/sudarshan/Games/kbilliards-0.8.7b'

======================== Installation successful ==========================

Copying documentation directory...
./
./ChangeLog
./INSTALL
./AUTHORS
./README
./doc/
./doc/Makefile
./doc/Makefile.am
./doc/en/
./doc/en/Makefile
./doc/en/index.docbook
./doc/en/Makefile.am
./doc/en/Makefile.in
./doc/Makefile.in
./NEWS
./TODO
./COPYING

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/sudarshan/Games/kbilliards-0.8.7b/kbilliards_0.8.7b-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r kbilliards

**********************************************************************
I am guessing the first few parts was to create documentation for checkinstall. Am i right?

Anyway, now how to do I start the game. It doesnt appear on the games menu on K-menu. I tried typing kbilliards on konsole and got a command not found...

---

### Post by Bachstelze on 2007-06-20
```
kde-config --prefix
```

what gives ?

---

### Post by linuxnovice on 2007-06-20
kde-config --prefix gives /usr

---

### Post by Bachstelze on 2007-06-20
Then it would be better to install the gamre in /usr than in /usr/local. Do this

```
sudo make clean
./configure --prefix=/usr
make
sudo checkinstall
```

---

### Post by linuxnovice on 2007-06-20
WOW!
I never thought I could ever compile any program from source..but thanks to help from all of you I ACTUALLY DID IT. thanks guys..it works beautifully..in fact it even shows up at the games menu.

I have 2 more questions:

1) Since I used checkinstall, I can uninstall the game using the .deb file right? I mean goin to package manager and uninstalling it?
2) Suppose my friend wants to try out this game and he is using kubuntu too..i could just hand over this .deb package created by checkinstall and he just install it easily and not worry about installing thro source right?
3) How do mark this thread as resolved?

THANKYOU! :)

---

### Post by atria on 2007-06-20
Glad it worked for you ;)

---

### Post by Bachstelze on 2007-06-20
1) Yes

2) I'd say yes, but maybe there wille be a few dependencies to install before the game runs.

3) Done :)

---

