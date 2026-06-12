---
title: "can't install things?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by thesqudge on 2008-01-30
Ok i keeps trying to install avant window navigator, i keep getting something fixed or resolved and i keep getting closer but now i get this message when i type in terminal:
```
./configure
```

and i already used the cd command to get to the folder containing the source code

so when i use the configure command i get this:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for intltool >= 0.34... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

and when i type the command:
```
make
```
i get this:
```
make: *** No targets specified and no makefile found.  Stop.
```
It's pretty long and i'm not sure where i went wrong... any thoughts?

---

### Post by LaRoza on 2008-01-30
It is much easier to install through synaptic.

Go to System->Admistration->Synaptic Package Manage and search for Avant Window Navagator

---

### Post by p_quarles on 2008-01-30
You're missing a bunch of dependencies for AWN. Which guide are you following (a link, if possible)?

EDIT: @LaRoza: That one's not in the repos, unfortunately.

---

### Post by lswest on 2008-01-30
to install through apt-get:
1) open a terminal and type ```
gksudo gedit /etc/apt/sources.list
```
2) append this: ```
## Avant Window Navigator
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
``` to the end of that file
3) run ```
sudo apt-get install avant-window-manager
```

(AWN is not in the default repositories)

---

### Post by thesqudge on 2008-01-30
ummm, i tryed the first suggestion with synaptic thing and i found avant and installed it and now it's in my accesories in applications. i can't tell if it's working or not because when i click the Avant icon something flashes at the bottom of my screen that's it, is there like a preferences i have to set up before any thing works? i'm not even sure if it was installed properly then if there should be a dock instantly...

---

### Post by p_quarles on 2008-01-30
It might be set on auto-hide. Try hovering the mouse/touchpad icon over the bottom center of the screen.

---

### Post by regomodo on 2008-01-30
"No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found"

that'll be why. Search for those in synaptic and install them first

---

### Post by thesqudge on 2008-01-30
nope, didn't work

---

### Post by thesqudge on 2008-01-30
oh...hmmm i'll try that

---

### Post by LaRoza on 2008-01-30
It is easy to add the repos though.

[http://wiki.awn-project.org/index.php?title=DistributionGuides](http://wiki.awn-project.org/index.php?title=DistributionGuides)

Just copy and paste the currect commands.

---

### Post by thesqudge on 2008-01-30
Har Har i fixed my problems! i just installed my video card drivers! DUHHH!! man i am the definition of noob! oh well as long as it works! yzay! thank you everyone, you guys gave me some good ideas and pointed me in the right direction! thankx:)

---

