---
title: "HELP!   Wacom Tablet is not recognized or responding in Feisty Fawn"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by ktwbug on 2007-09-24
Hi.  I'm fairly new to Ubuntu, but I am running a Toshiba laptop with Feisty Fawn 7.04.  I just recently bought a Bamboo Fun Wacom Tablet because it seemed that Ubuntu would have no problem reading it.  Turns out that my computer doesn't recognize it at all..... and the blue light on the tablet doesn't come on except for a second when I first plug it into the USB.  I've tried making sure that the wacom driver and tools are installed but still nothing- even after multiple reboots.  I'm not quiet sure what to do and I'm starting to wonder if there is something wrong with the tablet??  Anybody have anything that may help???  I'm o.k. with code....o.k.....not good, so I need pretty specific directions....hehe.....HELP!!!  

-Ubuntu fan that just wants to use her new drawing toy.

---

### Post by DirtDawg on 2007-09-25
There is a [community page]("https://help.ubuntu.com/community/Wacom") concerning Wacom Tablets, but even if you haven't found it already, it pretty much states that, starting with Feisty, Wacoms should be basically plug-n-play. Maybe there's something in there you overlooked?

My Wacom works fine, although I sometimes need to Ctrl+Alt+Backspace to get things working perfectly. I'm not familiar with the bamboo line of Wacom, but if they are brand-spanking new, it is possible the driver doesn't play nice yet. 

What a bummer. Hope you get things worked out.

---

### Post by Dan_Dranath999 on 2007-10-30
I just bought a Wacom Bamboo One, and couldn't make it work in Feisty... the driver in the Ubuntu repositories does't support it. (There's a version at SOURCEFORGE.NET that does, but i mess my sistem trying to install it ! AAARGH... CAN'T... COMPILE... PROPERLY!)

When the wacom driver in the repositories is updated, us silly newbies will be able to use our bamboo.

---

### Post by DirtDawg on 2007-10-31
> **Dan_Dranath999 said:**
> I just bought a Wacom Bamboo One, and couldn't make it work in Feisty... the driver in the Ubuntu repositories does't support it. (There's a version at SOURCEFORGE.NET that does, but i mess my sistem trying to install it ! AAARGH... CAN'T... COMPILE... PROPERLY!)

When the wacom driver in the repositories is updated, us silly newbies will be able to use our bamboo.

Have you checked to see if Gutsy provides the newer driver that supports bamboo?

---

### Post by Dan_Dranath999 on 2007-11-01
both Feisty n Gutsy have the linuxwacom-0.7.7.7 in the repositories, and we need the linuxwacom-0.7.8-3 for the Bamboo series...

---

### Post by DirtDawg on 2007-11-01
> **Dan_Dranath999 said:**
> both Feisty n Gutsy have the linuxwacom-0.7.7.7 in the repositories, and we need the linuxwacom-0.7.8-3 for the Bamboo series...

Too bad! I'm not sure how experienced you are with compiling, but if you'd like to post your errors maybe we can help? 

I totally understand the need for a tablet and I have a feeling there's no easy way to get it to work.

---

### Post by Dan_Dranath999 on 2007-11-02
i have been trying to compile the drivers (the "Linux Wacom Project HOWTO" is a lil'bit confusing for a Newbie) but i ONLY NEED 1 MORE THING TO DO IT RIGHT (i think) 

...The Xorg SDK build Enviroment (something like xorg-x11-sdk package) but i couldn't find it with apt-get or with synaptics (downloaded a rpm and tried to install it with alien but it gave me error messages) ¿WHERE DO I GET THAT THING? :confused:

This is the output from running ./configure (still not sure to run just ./configure or ./configure --enable-wacom) 

> daniel@daniel-desktop:~/linuxwacom-0.7.8-3$ sudo ./configure
[sudo] password for daniel:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gawk... (cached) gawk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for arch type... i486-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel sources... /lib/modules/2.6.22-14-generic/build
checking for kernel module support... yes
checking for kernel module versioning... yes
checking for valid Xorg SDK... "xf86Version.h missing"
Tried /usr/include, /usr/include/xorg and /usr/xc/include
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for stack-protector flags support in gcc... yes
checking for X lib directory... found
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... /usr/include/tcl8.4/
checking for tk header files... found
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
***
*** WARNING:
*** Unable to compile wacom_drv.{o,so} 
*** without Xorg SDK or XFree86 build environment
*** wacom_drv.o will not be built
***
checking if gcc accepts -fno-merge-constants... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.4/Makefile
config.status: creating src/2.4.22/Makefile
config.status: creating src/2.6.8/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i486-linux-gnu
       linux kernel - yes 2.6.19
  module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h
      kernel source - yes /lib/modules/2.6.22-14-generic/build
           Xorg SDK - no /usr
          XSERVER64 - no
           dlloader - no
               XLib - yes /usr/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
        tabletdev.o - no
       wacom_drv.so - no
        wacom_drv.o - no /usr/lib/xorg/modules/input 
----------------------------------------


---

### Post by Dan_Dranath999 on 2007-11-02
got the Xorg SDK finally!

BUT got this errors when running the MAKE command:


> make  all-recursive
make[1]: se ingresa al directorio `/home/daniel/linuxwacom-0.7.8-3'
Making all in src
make[2]: se ingresa al directorio `/home/daniel/linuxwacom-0.7.8-3/src'
Making all in .
make[3]: se ingresa al directorio `/home/daniel/linuxwacom-0.7.8-3/src'
make[3]: No se hace nada para `all-am'.
make[3]: se sale del directorio `/home/daniel/linuxwacom-0.7.8-3/src'
Making all in wacomxi
make[3]: se ingresa al directorio `/home/daniel/linuxwacom-0.7.8-3/src/wacomxi'
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -g -O2 -I/usr/include/tcl8.4/   -o libwacomxi.la -rpath /usr/local/lib/TkXInput -no-undefined wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0
/usr/bin/ld: cannot find -lXi
collect2: ld returned 1 exit status
make[3]: *** [libwacomxi.la] Error 1
make[3]: se sale del directorio `/home/daniel/linuxwacom-0.7.8-3/src/wacomxi'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/daniel/linuxwacom-0.7.8-3/src'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/daniel/linuxwacom-0.7.8-3'
make: *** [all] Error 2

what does that mean???

---

### Post by DirtDawg on 2007-11-02
Okay I'm going to suggest a total shot in the dark, so follow this advice at your own risk. There's a thread [here]("http://ubuntuforums.org/showthread.php?t=213986") with a similar error message (cannot find -lXi). He installed the following packages to solve the issue:
```
sudo apt-get install X-dev libX11-dev libXi-dev libXmu-dev
```

Be forewarned, I have no idea what any of these things do! It looks like they might have something to do with the underlying windows system, which would be some real nuts 'n' bolts stuff. Maybe someone who knows about these things can chime in.

Let us know how it goes.

---

