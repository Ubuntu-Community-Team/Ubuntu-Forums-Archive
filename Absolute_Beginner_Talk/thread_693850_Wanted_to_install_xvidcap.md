---
title: "Wanted to install xvidcap"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-11
Hello, I really wanted to install xvidcap, the latest version, I want to compile it so that it will be optimized on my Pentium M laptop... here are the messages I received...

```
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ sudo apt-get libglade-2.0
[sudo] password for karlo:
E: Invalid operation libglade-2.0
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ sudo apt-get install libglade-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libglade-2.0
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ make compile
make: *** No rule to make target `compile'.  Stop.
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ cd .
karlo@karlo-laptop:~/Downloads/xvidcap-1.1.6$ cd ..
karlo@karlo-laptop:~/Downloads$ cd System
karlo@karlo-laptop:~/Downloads/System$ cd libglade-2.0.1
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking if debuging support was requested... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
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
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.12.0)
checking for gtk_plug_get_type... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for libxml-2.0 >= 2.4.10 atk >= 1.0.0 gtk+-2.0 >= 2.0.0... yes
checking LIBGLADE_CFLAGS... -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking LIBGLADE_LIBS... -lxml2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for gtkdoc-mkdb... false
checking for ranlib... (cached) ranlib
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for getcwd... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 10204: ./po/POTFILES.in: No such file or directory
checking for Python >= 2.0 with expat support... /usr/bin/python
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libglade.spec
config.status: creating glade/Makefile
config.status: creating doc/Makefile
config.status: creating tests/Makefile
config.status: creating libglade-2.0.pc
config.status: creating libglade-convert
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands

This is the development branch of libglade
If you want something that works with gtk+ 1.2, checkout the
libglade-1-0 branch with the following command
  cvs update -r libglade-1-0 .

karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ make install
Making install in glade
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
source='glade-init.c' object='glade-init.lo' libtool=yes \
        depfile='.deps/glade-init.Plo' tmpdepfile='.deps/glade-init.TPlo' \
        depmode=gcc3 /bin/bash ../depcomp \
        /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12   -DGLADE_LIBDIR=\""/usr/local/lib"\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED    -g -O2 -Wall -std=c9x -c -o glade-init.lo `test -f 'glade-init.c' || echo './'`glade-init.c
mkdir .libs
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DGLADE_LIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -g -O2 -Wall -std=c9x -c glade-init.c -MT glade-init.lo -MD -MP -MF .deps/glade-init.TPlo  -fPIC -DPIC -o .libs/glade-init.lo
In file included from glade-init.c:34:
glade-private.h:33: error: expected specifier-qualifier-list before 'GtkTooltips'
make[1]: *** [glade-init.lo] Error 1
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
make: *** [install-recursive] Error 1
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ sudo make install
Making install in glade
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
source='glade-init.c' object='glade-init.lo' libtool=yes \
        depfile='.deps/glade-init.Plo' tmpdepfile='.deps/glade-init.TPlo' \
        depmode=gcc3 /bin/bash ../depcomp \
        /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12   -DGLADE_LIBDIR=\""/usr/local/lib"\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED    -g -O2 -Wall -std=c9x -c -o glade-init.lo `test -f 'glade-init.c' || echo './'`glade-init.c
rm -f .libs/glade-init.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DGLADE_LIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -g -O2 -Wall -std=c9x -c glade-init.c -MT glade-init.lo -MD -MP -MF .deps/glade-init.TPlo  -fPIC -DPIC -o .libs/glade-init.lo
In file included from glade-init.c:34:
glade-private.h:33: error: expected specifier-qualifier-list before 'GtkTooltips'
make[1]: *** [glade-init.lo] Error 1
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
make: *** [install-recursive] Error 1
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking if debuging support was requested... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
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
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.lo... yes
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.12.0)
checking for gtk_plug_get_type... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for libxml-2.0 >= 2.4.10 atk >= 1.0.0 gtk+-2.0 >= 2.0.0... yes
checking LIBGLADE_CFLAGS... -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12  
checking LIBGLADE_LIBS... -lxml2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for gtkdoc-mkdb... false
checking for ranlib... (cached) ranlib
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for getcwd... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 10204: ./po/POTFILES.in: No such file or directory
checking for Python >= 2.0 with expat support... /usr/bin/python
configure: creating ./config.status
config.status: creating Makefile
config.status: creating libglade.spec
config.status: creating glade/Makefile
config.status: creating doc/Makefile
config.status: creating tests/Makefile
config.status: creating libglade-2.0.pc
config.status: creating libglade-convert
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands

This is the development branch of libglade
If you want something that works with gtk+ 1.2, checkout the
libglade-1-0 branch with the following command
  cvs update -r libglade-1-0 .

karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ make
make  all-recursive
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1'
Making all in glade
make[2]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
source='glade-init.c' object='glade-init.lo' libtool=yes \
        depfile='.deps/glade-init.Plo' tmpdepfile='.deps/glade-init.TPlo' \
        depmode=gcc3 /bin/bash ../depcomp \
        /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12   -DGLADE_LIBDIR=\""/usr/local/lib"\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED    -g -O2 -Wall -std=c9x -c -o glade-init.lo `test -f 'glade-init.c' || echo './'`glade-init.c
rm -f .libs/glade-init.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DGLADE_LIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -g -O2 -Wall -std=c9x -c glade-init.c -MT glade-init.lo -MD -MP -MF .deps/glade-init.TPlo  -fPIC -DPIC -o .libs/glade-init.lo
In file included from glade-init.c:34:
glade-private.h:33: error: expected specifier-qualifier-list before 'GtkTooltips'
make[2]: *** [glade-init.lo] Error 1
make[2]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1'
make: *** [all] Error 2
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ install
install: missing file operand
Try `install --help' for more information.
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ make install
Making install in glade
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
source='glade-init.c' object='glade-init.lo' libtool=yes \
        depfile='.deps/glade-init.Plo' tmpdepfile='.deps/glade-init.TPlo' \
        depmode=gcc3 /bin/bash ../depcomp \
        /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12   -DGLADE_LIBDIR=\""/usr/local/lib"\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED    -g -O2 -Wall -std=c9x -c -o glade-init.lo `test -f 'glade-init.c' || echo './'`glade-init.c
rm -f .libs/glade-init.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DGLADE_LIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -g -O2 -Wall -std=c9x -c glade-init.c -MT glade-init.lo -MD -MP -MF .deps/glade-init.TPlo  -fPIC -DPIC -o .libs/glade-init.lo
In file included from glade-init.c:34:
glade-private.h:33: error: expected specifier-qualifier-list before 'GtkTooltips'
make[1]: *** [glade-init.lo] Error 1
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
make: *** [install-recursive] Error 1
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ configure
bash: configure: command not found
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ make
make  all-recursive
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1'
Making all in glade
make[2]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
source='glade-init.c' object='glade-init.lo' libtool=yes \
        depfile='.deps/glade-init.Plo' tmpdepfile='.deps/glade-init.TPlo' \
        depmode=gcc3 /bin/bash ../depcomp \
        /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12   -DGLADE_LIBDIR=\""/usr/local/lib"\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED    -g -O2 -Wall -std=c9x -c -o glade-init.lo `test -f 'glade-init.c' || echo './'`glade-init.c
rm -f .libs/glade-init.lo
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"libglade\" -I.. -I/usr/include/libxml2 -I/usr/include/atk-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DGLADE_LIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGDK_PIXBUF_DISABLE_DEPRECATED -DGTK_DISABLE_DEPRECATED -DGNOME_DISABLE_DEPRECATED -g -O2 -Wall -std=c9x -c glade-init.c -MT glade-init.lo -MD -MP -MF .deps/glade-init.TPlo  -fPIC -DPIC -o .libs/glade-init.lo
In file included from glade-init.c:34:
glade-private.h:33: error: expected specifier-qualifier-list before 'GtkTooltips'
make[2]: *** [glade-init.lo] Error 1
make[2]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1'
make: *** [all] Error 2
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ make clean
Making clean in tests
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1/tests'
 rm -f test-libglade-gtk test-libglade-gtk
 rm -f test-value-parse test-value-parse
test -z "test-libglade-gtk.glade2 test-libglade-gtk-noupgrade.glade2 .memdump" || rm -f test-libglade-gtk.glade2 test-libglade-gtk-noupgrade.glade2 .memdump
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1/tests'
Making clean in doc
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1/doc'
rm -rf .libs _libs
rm -f *~ *.bak *.hierarchy *.signals *-unused.txt
rm -f libglade-scan.lo libglade-scan.o libglade-scan
rm -f *.stamp
rm -f *.lo
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1/doc'
Making clean in glade
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
test -z "libglade-2.0.la" || rm -f libglade-2.0.la
rm -f "libglade-2.0.la/so_locations"
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.lo
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1/glade'
Making clean in .
make[1]: Entering directory `/home/karlo/Downloads/System/libglade-2.0.1'
rm -rf .libs _libs
rm -f intl/po2tbl.sed .memdump
 rm -f test-libglade test-libglade
rm -f *.o core *.core
rm -f *.lo
make[1]: Leaving directory `/home/karlo/Downloads/System/libglade-2.0.1'
karlo@karlo-laptop:~/Downloads/System/libglade-2.0.1$ 
```

---

### Post by harold4 on 2008-02-11
```
sudo apt-get install libglade2-dev
```

Then try from the beginning.

---

