---
title: "trying to install twitux"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-03-28
Hello,

I want to install a twitter client. I downloaded the Twitux package. I am trying to install it from terminal, but it doesn't work and I'm not sure why. The instructions simply said to cd to the source code, which I did, and then run ./configure, which I did. After I do that I try to run make, and it says "no targets specified and no makefile found." ?

The output on the screen immediately after I run ./configure is very long, but at the end I see some things are "missing." Here is what it says:
```

gslik@GSLIK-LOGIC:~/Desktop/twitux-0.61$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
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
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for intltool >= 0.35.0... 0.37.1 found
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking whether gcc understands -Wno-sign-compare... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare
checking what language compliance flags to pass to the C compiler... 
checking what warning flags to pass to the C++ compiler... 
checking what language compliance flags to pass to the C++ compiler... 
checking whether iso-codes exists and has iso-639 domain... yes
checking for DBUS... no
checking for GNOME_KEYRING... no
checking for LIBTWITUX... configure: error: Package requirements (
        libxml-2.0 >= 2.6.16
        glib-2.0 >= 2.15.0
        gtk+-2.0 >= 2.10.0
        gobject-2.0
        gconf-2.0 >= 1.2.0

) were not met:

No package 'libxml-2.0' found
No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'gobject-2.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBTWITUX_CFLAGS
and LIBTWITUX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Any ideas? 

Thanks. I haven't had much success installing anything from terminal...

---

### Post by zvacet on 2008-03-28
You didn´t do anything wrong.Problem is that you need Hardy to install it.You can install 0.60 version from [here.](http://www.getdeb.net/search.php?keywords=Twitux)

---

### Post by Nutopia on 2008-03-28
thank you, hero! worked!!

---

### Post by kr0ots on 2008-04-08
Hey guys, 

i found a .deb of twitux here : [http://live.gnome.org/DanielMorales/Twitux](http://live.gnome.org/DanielMorales/Twitux).
you don't need to compile it at all.

But something is wrong, they about 0.61 vers. and i still have the 0.60 after installing the package. I bet its because some of dependance are not install, but ican't find it. :)
Is it because i running Hardy?

---

### Post by moeFinley on 2008-04-29
[Gnome Do]("https://wiki.ubuntu.com/GnomeDo") is a great why to make Twitter posts

---

