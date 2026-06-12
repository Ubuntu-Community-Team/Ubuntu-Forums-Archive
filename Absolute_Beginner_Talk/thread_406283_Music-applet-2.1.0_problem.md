---
title: "Music-applet-2.1.0 problem"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by false_cognate on 2007-04-10
Hi all.

I've been using Ubuntu for about a month to a month and a half now, and although it was difficult at first, I'm getting better. But on to the problem...

The version of music-applet in the repo is an old one that supports less media players, and doesn't show album art when hovered. Since I've now managed to be able to install things from tarballed packages, I got the latest version from the project page (2.1.0).

Unfortunately, when I ran the configure script, it came up with a missing dependency: libpanelapplet-2.0. I did some poking around, and it turns out that I have it, but it's named "libpanelapplet-2-0".

Not knowing what to do, I opened the configure file in gedit and proceeded to do replace every instance of "libpanelapplet-2.0" with "libpanelapplet-2-0", hoping it would work.

I ran the configure again, and it said the dependency was still missing, although it now gave the correct name of it as it is on my system.

Any ideas?

---

### Post by false_cognate on 2007-04-10
so there is nothing i can do?

---

### Post by dakota1 on 2007-04-23
I'm having the same problem. 

Anybody have a solution for it?

---

### Post by dakota1 on 2007-04-25
Managed to get it to compile by installing the libpanelapplet-2.0-dev package. but I can't get it to actually install, no erros, it just doesn't show up in the add to panel window

---

### Post by ernz on 2007-05-28
***IMPORTANT SIDE NOTE***
[COLOR="White"]keywords: add to panel, exaile, music, applet, music-applet, missing, problem, 2.1.0[/COLOR]
I finally managed to get my music-applet version 2.1.0 compiled installed alongside Exaile 2.10 SVN Version using the advise here, however the applet didn't show in the "Add to Panel" menu. I spent several hours restarting X and killing gnome-panel and reloading it, but it just didn't work. I gave up thinking I must just have a dud install of Feisty or something.

I restarted this morning and guess what I found... a shiny new applet sitting in the Add to Panel menu!

Moral of the story: If you think this is properly installed, it probably is. Restart the PC, not just X server, and it might work for you too. :D

---

### Post by bortx on 2007-05-28
In order to show music applet in the Add to panel menu, you should do what is said in music applet FAQ:

[http://www.kuliniewicz.org/music-applet/faq.html](http://www.kuliniewicz.org/music-applet/faq.html)

---

### Post by Monosabio on 2007-05-30
I can't add the music-applet 2.10 to gnome panel. I have restarted the computer but still can't add the applet.
I did all 3 steps to install it: 1) /.configure 2) make 3) sudo make install
Am I missing something ?

**./configure**

```

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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether to enable strict checks... (cached) no
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... found
checking for pygtk-codegen-2.0... /usr/bin/pygtk-codegen-2.0
checking for pkg-config... /usr/bin/pkg-config
checking for pygtk-2.0... yes
checking PYGTK_CODEGENDIR... /usr/share/pygtk/2.0/codegen
checking for pygtk-2.0... yes
checking PYGTK_DEFSDIR... /usr/share/pygtk/2.0/defs
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for intltool >= 0.33... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking pkg-config is at least version 0.9.0... yes
checking for MUSICAPPLET_DEPS... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/musicapplet/Makefile
config.status: creating src/musicapplet/defs.py.in
config.status: creating src/musicapplet/plugins/Makefile
config.status: creating data/Makefile
config.status: creating templates/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

```

**make**

```

make  all-recursive
make[1]: Entering directory `/home/linux/Desktop/music-applet-2.1'
Making all in src
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1/src'
Making all in musicapplet
make[3]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
sed -e "s|@xDATADIRx@|/usr/local/share|"                \
            -e "s|@xLIBDIRx@|/usr/local/lib|"           \
            -e "s|@xPYTHONDIRx@|/usr/local/lib/python2.5/site-packages|"       \
            -e "s|@xPKGDATADIRx@|/usr/local/share/music-applet|"        \
            defs.py.in > defs.py
make  all-recursive
make[4]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
Making all in plugins
make[5]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet/plugins'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet/plugins'
make[5]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..     -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0   -MT ma-deserialize.lo -MD -MP -MF ".deps/ma-deserialize.Tpo" -c -o ma-deserialize.lo ma-deserialize.c; \
        then mv -f ".deps/ma-deserialize.Tpo" ".deps/ma-deserialize.Plo"; else rm -f ".deps/ma-deserialize.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0 -MT ma-deserialize.lo -MD -MP -MF .deps/ma-deserialize.Tpo -c ma-deserialize.c  -fPIC -DPIC -o .libs/ma-deserialize.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..     -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0   -MT ma-fancy-button.lo -MD -MP -MF ".deps/ma-fancy-button.Tpo" -c -o ma-fancy-button.lo ma-fancy-button.c; \
        then mv -f ".deps/ma-fancy-button.Tpo" ".deps/ma-fancy-button.Plo"; else rm -f ".deps/ma-fancy-button.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0 -MT ma-fancy-button.lo -MD -MP -MF .deps/ma-fancy-button.Tpo -c ma-fancy-button.c  -fPIC -DPIC -o .libs/ma-fancy-button.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..     -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0   -MT ma-fancy-tooltips.lo -MD -MP -MF ".deps/ma-fancy-tooltips.Tpo" -c -o ma-fancy-tooltips.lo ma-fancy-tooltips.c; \
        then mv -f ".deps/ma-fancy-tooltips.Tpo" ".deps/ma-fancy-tooltips.Plo"; else rm -f ".deps/ma-fancy-tooltips.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0 -MT ma-fancy-tooltips.lo -MD -MP -MF .deps/ma-fancy-tooltips.Tpo -c ma-fancy-tooltips.c  -fPIC -DPIC -o .libs/ma-fancy-tooltips.o
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..     -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0   -MT widgetsmodule.lo -MD -MP -MF ".deps/widgetsmodule.Tpo" -c -o widgetsmodule.lo widgetsmodule.c; \
        then mv -f ".deps/widgetsmodule.Tpo" ".deps/widgetsmodule.Plo"; else rm -f ".deps/widgetsmodule.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0 -MT widgetsmodule.lo -MD -MP -MF .deps/widgetsmodule.Tpo -c widgetsmodule.c  -fPIC -DPIC -o .libs/widgetsmodule.o
/usr/bin/python /usr/share/pygtk/2.0/codegen/h2def.py ma-deserialize.h ma-fancy-button.h ma-fancy-tooltips.h >widgets.defs
/usr/bin/pygtk-codegen-2.0 --prefix widgets                             \
                         --register /usr/share/pygtk/2.0/defs/gdk-types.defs   \
                         --register /usr/share/pygtk/2.0/defs/gtk-types.defs   \
                         --override widgets.override                    \
                         widgets.defs >widgets.c
***INFO*** The coverage of global functions is 100.00% (1/1)
***INFO*** The coverage of methods is 100.00% (8/8)
***INFO*** There are no declared virtual proxies.
***INFO*** There are no declared virtual accessors.
***INFO*** There are no declared interface proxies.
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../..     -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0   -MT widgets.lo -MD -MP -MF ".deps/widgets.Tpo" -c -o widgets.lo widgets.c; \
        then mv -f ".deps/widgets.Tpo" ".deps/widgets.Plo"; else rm -f ".deps/widgets.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0 -MT widgets.lo -MD -MP -MF .deps/widgets.Tpo -c widgets.c  -fPIC -DPIC -o .libs/widgets.o
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2 -g -Wall -W -Wno-unused -Wno-missing-field-initializers -I/usr/include/python2.5 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/panel-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0     -o widgets.la -rpath /usr/local/lib/python2.5/site-packages/musicapplet -module -avoid-version -export-symbols-regex initwidgets ma-deserialize.lo ma-fancy-button.lo ma-fancy-tooltips.lo widgetsmodule.lo widgets.lo  -Wl,--export-dynamic -pthread -lpanel-applet-2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnome-keyring -lgconf-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lbonobo-2 -lbonobo-activation -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0  
generating symbol list for `widgets.la'
/usr/bin/nm -B  .libs/ma-deserialize.o .libs/ma-fancy-button.o .libs/ma-fancy-tooltips.o .libs/widgetsmodule.o .libs/widgets.o  | sed -n -e 's/^.*[     ]\([ABCDGIRSTW][ABCDGIRSTW]*\)[         ][      ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' | /bin/sed 's/.* //' | sort | uniq > .libs/widgets.exp
/bin/grep -E -e "initwidgets" ".libs/widgets.exp" > ".libs/widgets.expT"
mv -f ".libs/widgets.expT" ".libs/widgets.exp"
echo "{ global:" > .libs/widgets.ver
 cat .libs/widgets.exp | sed -e "s/\(.*\)/\1;/" >> .libs/widgets.ver
 echo "local: *; };" >> .libs/widgets.ver
 gcc -shared  .libs/ma-deserialize.o .libs/ma-fancy-button.o .libs/ma-fancy-tooltips.o .libs/widgetsmodule.o .libs/widgets.o  /usr/lib/libpanel-applet-2.so /usr/lib/libgnomeui-2.so -lSM -lICE /usr/lib/libbonoboui-2.so /usr/lib/libgnomevfs-2.so /usr/lib/libgnome-keyring.so /usr/lib/libgconf-2.so /usr/lib/libgnomecanvas-2.so /usr/lib/libgnome-2.so /usr/lib/libpopt.so /usr/lib/libart_lgpl_2.so /usr/lib/libpangoft2-1.0.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -lX11 /usr/lib/libbonobo-2.so /usr/lib/libbonobo-activation.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libORBit-2.so /usr/lib/libgthread-2.0.so -lrt /usr/lib/libgobject-2.0.so /usr/lib/libglib-2.0.so  -pthread -Wl,--export-dynamic -pthread -Wl,-soname -Wl,widgets.so -Wl,-version-script -Wl,.libs/widgets.ver -o .libs/widgets.so
creating widgets.la
(cd .libs && rm -f widgets.la && ln -s ../widgets.la widgets.la)
make[5]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[4]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[3]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[3]: Entering directory `/home/linux/Desktop/music-applet-2.1/src'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src'
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src'
Making all in data
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1/data'
LC_ALL=C ../intltool-merge -s -u -c ../po/.intltool-merge-cache ../po music-applet.schemas.in music-applet.schemas
Generating and caching the translation database
NOTICE: ../po/es.po is not in UTF-8 but ISO-8859-1, converting...
NOTICE: ../po/fr.po is not in UTF-8 but ISO-8859-1, converting...
Merging translations into music-applet.schemas.
sed -e "s|\@LIBEXECDIR\@|/usr/local/libexec|" GNOME_Music_Applet.server.in.in | sed -e "s|\@PKGDATADIR\@|/usr/local/share/music-applet|" > GNOME_Music_Applet.server.in
LC_ALL=C ../intltool-merge -o -u -c ../po/.intltool-merge-cache ../po GNOME_Music_Applet.server.in GNOME_Music_Applet.server
Found cached translation database
Merging translations into GNOME_Music_Applet.server.
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1/data'
Making all in templates
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1/templates'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1/templates'
Making all in po
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file de.po
file=`echo es | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file es.po
file=`echo fr | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file fr.po
file=`echo it | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file it.po
file=`echo ja | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file ja.po
file=`echo nb | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file nb.po
file=`echo nl | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file nl.po
file=`echo pl | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file pl.po
file=`echo pt_BR | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file pt_BR.po
file=`echo sv | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file sv.po
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1/po'
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1'
make[1]: Leaving directory `/home/linux/Desktop/music-applet-2.1'

```

**sudo make install**

```

Making install in src
make[1]: Entering directory `/home/linux/Desktop/music-applet-2.1/src'
Making install in musicapplet
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make  install-recursive
make[3]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
Making install in plugins
make[4]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet/plugins'
make[5]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet/plugins'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/python2.5/site-packages/musicapplet/plugins" || mkdir -p -- "/usr/local/lib/python2.5/site-packages/musicapplet/plugins"
 /usr/bin/install -c -m 644 '__init__.py' '/usr/local/lib/python2.5/site-packages/musicapplet/plugins/__init__.py'
 /usr/bin/install -c -m 644 'banshee.py' '/usr/local/lib/python2.5/site-packages/musicapplet/plugins/banshee.py'
 /usr/bin/install -c -m 644 'exaile.py' '/usr/local/lib/python2.5/site-packages/musicapplet/plugins/exaile.py'
 /usr/bin/install -c -m 644 'muine.py' '/usr/local/lib/python2.5/site-packages/musicapplet/plugins/muine.py'
 /usr/bin/install -c -m 644 'rhythmbox.py' '/usr/local/lib/python2.5/site-packages/musicapplet/plugins/rhythmbox.py'
 /usr/bin/install -c -m 644 'xmms2.py' '/usr/local/lib/python2.5/site-packages/musicapplet/plugins/xmms2.py'
Byte-compiling python modules...
__init__.py banshee.py exaile.py muine.py rhythmbox.py xmms2.py
Byte-compiling python modules (optimized versions) ...
__init__.py banshee.py exaile.py muine.py rhythmbox.py xmms2.py
make[5]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet/plugins'
make[4]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet/plugins'
make[4]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[5]: Entering directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[5]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/python2.5/site-packages/musicapplet" || mkdir -p -- "/usr/local/lib/python2.5/site-packages/musicapplet"
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'widgets.la' '/usr/local/lib/python2.5/site-packages/musicapplet/widgets.la'
/usr/bin/install -c .libs/widgets.so /usr/local/lib/python2.5/site-packages/musicapplet/widgets.so
/usr/bin/install -c .libs/widgets.lai /usr/local/lib/python2.5/site-packages/musicapplet/widgets.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib/python2.5/site-packages/musicapplet
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/python2.5/site-packages/musicapplet

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/lib/python2.5/site-packages/musicapplet" || mkdir -p -- "/usr/local/lib/python2.5/site-packages/musicapplet"
 /usr/bin/install -c -m 644 '__init__.py' '/usr/local/lib/python2.5/site-packages/musicapplet/__init__.py'
 /usr/bin/install -c -m 644 'applet.py' '/usr/local/lib/python2.5/site-packages/musicapplet/applet.py'
 /usr/bin/install -c -m 644 'conf.py' '/usr/local/lib/python2.5/site-packages/musicapplet/conf.py'
 /usr/bin/install -c -m 644 'manager.py' '/usr/local/lib/python2.5/site-packages/musicapplet/manager.py'
 /usr/bin/install -c -m 644 'player.py' '/usr/local/lib/python2.5/site-packages/musicapplet/player.py'
 /usr/bin/install -c -m 644 'util.py' '/usr/local/lib/python2.5/site-packages/musicapplet/util.py'
Byte-compiling python modules...
__init__.py applet.py conf.py manager.py player.py util.py
Byte-compiling python modules (optimized versions) ...
__init__.py applet.py conf.py manager.py player.py util.py
test -z "/usr/local/lib/python2.5/site-packages/musicapplet" || mkdir -p -- "/usr/local/lib/python2.5/site-packages/musicapplet"
 /usr/bin/install -c -m 644 'defs.py' '/usr/local/lib/python2.5/site-packages/musicapplet/defs.py'
Byte-compiling python modules...
defs.py
Byte-compiling python modules (optimized versions) ...
defs.py
make[5]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[4]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[3]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src/musicapplet'
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1/src'
make[3]: Entering directory `/home/linux/Desktop/music-applet-2.1/src'
test -z "/usr/local/libexec" || mkdir -p -- "/usr/local/libexec"
 /usr/bin/install -c 'music-applet' '/usr/local/libexec/music-applet'
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src'
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src'
make[1]: Leaving directory `/home/linux/Desktop/music-applet-2.1/src'
Making install in data
make[1]: Entering directory `/home/linux/Desktop/music-applet-2.1/data'
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1/data'
make[2]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults /usr/bin/gconftool-2 --makefile-install-rule music-applet.schemas ;
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
Installed schema `/schemas/apps/music-applet/prefs/show_rating' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/show_rating' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/show_time' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/show_time' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/show_controls' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/show_controls' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/preferred_player' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/banshee_launch' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/banshee_launch' for locale `it'
Installed schema `/schemas/apps/music-applet/prefs/banshee_launch' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/banshee_launch' for locale `nl'
Installed schema `/schemas/apps/music-applet/prefs/banshee_launch' for locale `sv'
Installed schema `/schemas/apps/music-applet/prefs/banshee_command' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/banshee_command' for locale `it'
Installed schema `/schemas/apps/music-applet/prefs/banshee_command' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/banshee_command' for locale `nl'
Installed schema `/schemas/apps/music-applet/prefs/banshee_command' for locale `sv'
Installed schema `/schemas/apps/music-applet/prefs/Muine/launch' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/Muine/launch' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/muine_command' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/muine_command' for locale `it'
Installed schema `/schemas/apps/music-applet/prefs/muine_command' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/muine_command' for locale `nl'
Installed schema `/schemas/apps/music-applet/prefs/muine_command' for locale `sv'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_conn_path' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_conn_path' for locale `it'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_conn_path' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_conn_path' for locale `nl'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_conn_path' for locale `sv'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_command' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_command' for locale `it'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_command' for locale `pl'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_command' for locale `nl'
Installed schema `/schemas/apps/music-applet/prefs/xmms2_command' for locale `sv'
Installed schema `/schemas/apps/music-applet/prefs/Exaile/launch' for locale `C'
Installed schema `/schemas/apps/music-applet/prefs/Exaile/command' for locale `C'
test -z "/usr/local/share/music-applet" || mkdir -p -- "/usr/local/share/music-applet"
 /usr/bin/install -c -m 644 'dbus.glade' '/usr/local/share/music-applet/dbus.glade'
 /usr/bin/install -c -m 644 'music-applet-set-star.png' '/usr/local/share/music-applet/music-applet-set-star.png'
 /usr/bin/install -c -m 644 'music-applet-unset-star.png' '/usr/local/share/music-applet/music-applet-unset-star.png'
 /usr/bin/install -c -m 644 'plugins.glade' '/usr/local/share/music-applet/plugins.glade'
 /usr/bin/install -c -m 644 'preferences.glade' '/usr/local/share/music-applet/preferences.glade'
 /usr/bin/install -c -m 644 'xmms2.glade' '/usr/local/share/music-applet/xmms2.glade'
test -z "/usr/local/etc/gconf/schemas" || mkdir -p -- "/usr/local/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'music-applet.schemas' '/usr/local/etc/gconf/schemas/music-applet.schemas'
test -z "/usr/local/lib/bonobo/servers" || mkdir -p -- "/usr/local/lib/bonobo/servers"
 /usr/bin/install -c -m 644 'GNOME_Music_Applet.server' '/usr/local/lib/bonobo/servers/GNOME_Music_Applet.server'
test -z "/usr/local/lib/gnome-2.0/ui" || mkdir -p -- "/usr/local/lib/gnome-2.0/ui"
 /usr/bin/install -c -m 644 'GNOME_Music_Applet.xml' '/usr/local/lib/gnome-2.0/ui/GNOME_Music_Applet.xml'
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1/data'
make[1]: Leaving directory `/home/linux/Desktop/music-applet-2.1/data'
Making install in templates
make[1]: Entering directory `/home/linux/Desktop/music-applet-2.1/templates'
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1/templates'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1/templates'
make[1]: Leaving directory `/home/linux/Desktop/music-applet-2.1/templates'
Making install in po
make[1]: Entering directory `/home/linux/Desktop/music-applet-2.1/po'
/home/linux/Desktop/music-applet-2.1/install-sh -d /usr/local/share/locale
if test -n "de es fr it ja nb nl pl pt_BR sv"; then \
          linguas="de es fr it ja nb nl pl pt_BR sv"; \
        else \
          linguas=""; \
        fi; \
        for lang in $linguas; do \
          dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
          /home/linux/Desktop/music-applet-2.1/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/music-applet.mo; \
            echo "installing $lang.gmo as $dir/music-applet.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/music-applet.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/music-applet.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/music-applet.mo.m; \
            echo "installing $lang.gmo.m as $dir/music-applet.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/music-applet.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/music-applet.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/music-applet.mo
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/music-applet.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/music-applet.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/music-applet.mo
installing ja.gmo as /usr/local/share/locale/ja/LC_MESSAGES/music-applet.mo
installing nb.gmo as /usr/local/share/locale/nb/LC_MESSAGES/music-applet.mo
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/music-applet.mo
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/music-applet.mo
installing pt_BR.gmo as /usr/local/share/locale/pt_BR/LC_MESSAGES/music-applet.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/music-applet.mo
make[1]: Leaving directory `/home/linux/Desktop/music-applet-2.1/po'
make[1]: Entering directory `/home/linux/Desktop/music-applet-2.1'
make[2]: Entering directory `/home/linux/Desktop/music-applet-2.1'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/linux/Desktop/music-applet-2.1'
make[1]: Leaving directory `/home/linux/Desktop/music-applet-2.1'

```

---

