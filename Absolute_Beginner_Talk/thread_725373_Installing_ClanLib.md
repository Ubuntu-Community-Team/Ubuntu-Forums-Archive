---
title: "Installing ClanLib"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by CloudFX on 2008-03-15
I'm trying to install ClanLib, and I've come across the error that I need to install a bunch of other 'Clan' stuff. I've gone through them all, and now the only one left is ClanGL. The problem with this is, it's too short to get an accurate search in Synaptic. What should I do to install this thing?

Also, here is the output from the ./configure command.

```
Ubuntu@UbuntuPC:~/Desktop/ClanLib-0.8.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
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
checking for pkg-config... /usr/bin/pkg-config
checking for unistd.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/kd.h usability... yes
checking sys/kd.h presence... yes
checking for sys/kd.h... yes
checking sys/vt.h usability... yes
checking sys/vt.h presence... yes
checking for sys/vt.h... yes
checking for i386... yes
checking for i386 assembly support... enabled
checking for dynamic loading support... disabled
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking for sys/types.h... (cached) yes
checking sys/ipc.h usability... yes
checking sys/ipc.h presence... yes
checking for sys/ipc.h... yes
checking sys/shm.h usability... yes
checking sys/shm.h presence... yes
checking for sys/shm.h... yes
checking fstab.h usability... yes
checking fstab.h presence... yes
checking for fstab.h... yes
checking for pthread_create in -lpthread... yes
checking for main in -lz... yes

Checking for ClanLib Modules to build...
========================================
checking whether we should try to build documentation... auto
checking whether we should try to build clanDisplay... auto
checking whether we should try to build clanSDL... auto
checking whether we should try to build clanGL... auto
checking whether we should try to build clanSound... auto
checking whether we should try to build clanNetwork... auto
checking whether we should try to build clanGUI... auto
checking whether we should try to build clanMikMod... auto
checking whether we should try to build clanVorbis... auto

Checking for clanDisplay stuff
==============================
checking for png... yes
checking for jpeg... yes
checking for X... libraries , headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... no
checking for library containing XF86VidModeQueryExtension... no
Checking for clanSDL stuff
==============================
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zoomSurface in -lSDL_gfx... no
configure: WARNING: SDL_gfx not found, clanSDL will not be able to use scaling and rotation!
Checking for clanGL stuff
==============================
checking for GL... yes
checking for XListInputDevices in -lXi... no
configure: WARNING:  *** Cannot find libXi (xinput). Disabling clanGL

Checking for clanSound stuff
============================
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes

checking for mikmod... yes
checking pkg-config is at least version 0.9.0... yes
checking for clanVorbis... yes

Checking for clanNetwork stuff
==============================
checking for getaddrinfo... yes
checking for GetAddr (ipv6) support... enabled

Checking for Documentation stuff
================================
checking for perl... /usr/bin/perl
checking for Xalan... no
checking for xsltproc... /usr/bin/xsltproc
checking if documentation should be generated... auto

Checking for debugging and profiling
====================================
checking for debug mode... disabled
checking for profile mode... disabled

checking for maintainer mode... disabled
configure: creating ./config.status
config.status: creating Sources/Core/Makefile
config.status: creating pkgconfig/clanCore.pc
config.status: creating Sources/Signals/Makefile
config.status: creating pkgconfig/clanSignals.pc
config.status: creating Sources/Display/Makefile
config.status: creating pkgconfig/clanDisplay.pc
config.status: creating Sources/Sound/Makefile
config.status: creating pkgconfig/clanSound.pc
config.status: creating Sources/SDL/Makefile
config.status: creating pkgconfig/clanSDL.pc
config.status: creating Sources/GUI/Makefile
config.status: creating pkgconfig/clanGUI.pc
config.status: creating Sources/GUIStyleSilver/Makefile
config.status: creating pkgconfig/clanGUIStyleSilver.pc
config.status: creating Sources/Network/Makefile
config.status: creating pkgconfig/clanNetwork.pc
config.status: creating Sources/MikMod/Makefile
config.status: creating pkgconfig/clanMikMod.pc
config.status: creating Sources/Vorbis/Makefile
config.status: creating pkgconfig/clanVorbis.pc
config.status: creating Documentation/Utilities/xslt.sh
config.status: creating Documentation/Utilities/webbuilder.pl
config.status: creating Documentation/Reference/pce2
config.status: creating Documentation/Makefile
config.status: creating Documentation/Overview/Makefile
config.status: creating Documentation/Reference/Makefile
config.status: creating Documentation/Tutorial/Makefile
config.status: creating Documentation/Tutorial/Kavanek/Makefile
config.status: creating pkgconfig/clanApp.pc
config.status: creating pkgconfig/Makefile
config.status: creating Makefile
config.status: creating Examples/Makefile
config.status: creating Examples/Makefile.conf
config.status: creating Setup/Makefile
config.status: creating Sources/API/Makefile
config.status: creating Sources/Application/Makefile
config.status: creating Sources/Makefile
config.status: creating Tests/Makefile.conf
config.status: executing depfiles commands
------------------------------------------------------------------------------
The following modules will be built:

                     clanGL = no
                    clanSDL = yes
                    clanApp = yes
                    clanGUI = yes
                   clanCore = yes
                  clanSound = yes
                clanNetwork = yes
                clanSignals = yes
                clanDisplay = yes
                 clanMikmod = yes
                 clanVorbis = yes

        Build Documentation = yes
                Debug Build = no
```

---

### Post by kellemes on 2008-03-15
You need to install "libclan2c2a-gl"
See here.. [http://packages.ubuntu.com/gutsy/libclan2c2a-gl]("http://packages.ubuntu.com/gutsy/libclan2c2a-gl")

---

### Post by CloudFX on 2008-03-15
that file is shown as already installed, and the ClanGL row still says 'no'.

---

### Post by kellemes on 2008-03-15
> **CloudFX said:**
> that file is shown as already installed, and the ClanGL row still says 'no'.

I guess you need the development files.. since you're building here. Again, just guessing here ;-)
[libclanlib-dev]("http://packages.ubuntu.com/gutsy/libclanlib-dev")

---

### Post by CloudFX on 2008-03-15
should i get all of those?

---

