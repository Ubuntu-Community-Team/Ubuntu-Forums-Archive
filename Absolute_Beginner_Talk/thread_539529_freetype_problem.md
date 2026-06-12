---
title: "freetype problem"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Chiclette on 2007-08-31
Hey, 

i'm a beginner in Ubuntu, i am experiencing a problem installing some packages:

I need gtk+ for installing pidgin 2.0

for gtk+ i need the pango package

pango is acting kinda weird: 

brecht@brecht-desktop:~/Desktop/pango-1.16.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for native Win32... no
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
checking for c++... c++
checking whether we are using the GNU C++ compiler... yes
checking whether c++ accepts -g... yes
checking dependency style of c++... gcc3
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
checking how to run the C++ preprocessor... c++ -E
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
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by c++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the c++ linker (/usr/bin/ld) supports shared libraries... yes
checking for c++ option to produce PIC... -fPIC
checking if c++ PIC flag -fPIC works... yes
checking if c++ static flag -static works... yes
checking if c++ supports -c -o file.o... yes
checking whether the c++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for some Win32 platform... no
checking for perl5... no
checking for perl... perl
checking for X... no
configure: WARNING: X development libraries not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for FONTCONFIG... yes
checking for freetype-config... /usr/local/bin/freetype-config
checking for FT_Get_Next_Char in -lfreetype... yes
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking for CAIRO... yes
checking for cairo_surface_write_to_png in -lcairo... yes
checking for cairo_ps_surface_create in -lcairo... yes
checking for cairo_pdf_surface_create in -lcairo... yes
checking for cairo_xlib_surface_create in -lcairo... no
checking for cairo_win32_scaled_font_select_font in -lcairo... no
checking for cairo_ft_scaled_font_lock_face in -lcairo... yes
checking for cairo_atsui_font_face_create_for_atsu_font_id in -lcairo... no
checking for GLIB... yes
checking for LIBTHAI... no
no
checking modules to link statically...
checking dynamic modules to build... arabic-fc,arabic-lang,basic-fc,basic-win32,basic-x,basic-atsui,hangul-fc,hebrew-fc,indic-fc,indic-lang,khmer-fc,syriac-fc,thai-fc,tibetan-fc (those built into Pango will be excluded)
checking for flockfile... yes
checking for strtok_r... yes
checking Whether to write dependencies into .pc files... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for unistd.h... (cached) yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pango/Makefile
config.status: creating pango/mini-fribidi/Makefile
config.status: creating pango/opentype/Makefile
config.status: creating pango/pango.rc
config.status: creating pango/pangoft2.rc
config.status: creating pango/pangowin32.rc
config.status: creating pango-view/Makefile
config.status: creating modules/Makefile
config.status: creating modules/arabic/Makefile
config.status: creating modules/basic/Makefile
config.status: creating modules/hangul/Makefile
config.status: creating modules/hebrew/Makefile
config.status: creating modules/indic/Makefile
config.status: creating modules/khmer/Makefile
config.status: creating modules/syriac/Makefile
config.status: creating modules/thai/Makefile
config.status: creating modules/tibetan/Makefile
config.status: creating examples/Makefile
config.status: creating docs/Makefile
config.status: creating docs/version.xml
config.status: creating tools/Makefile
config.status: creating tests/Makefile
config.status: creating pango.pc
config.status: creating pangox.pc
config.status: creating pangowin32.pc
config.status: creating pangoft2.pc
config.status: creating pangoxft.pc
config.status: creating pangocairo.pc
config.status: creating pango-uninstalled.pc
config.status: creating pangox-uninstalled.pc
config.status: creating pangowin32-uninstalled.pc
config.status: creating pangoft2-uninstalled.pc
config.status: creating pangoxft-uninstalled.pc
config.status: creating pangocairo-uninstalled.pc
config.status: creating pango-zip.sh
config.status: creating tests/runtests.sh
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing pango/module-defs.h commands
config.status: executing pango/module-defs-x.c commands
config.status: executing pango/module-defs-fc.c commands
config.status: executing pango/module-defs-win32.c commands
config.status: executing pango/module-defs-atsui.c commands
config.status: executing pango/module-defs-lang.c commands
config.status: executing pango/pango-features.h commands
config.status: creating pango/pango-features.h
config.status: pango/pango-features.h is unchanged
configuration:
        backends: FreeType Cairo

:KS

So i think the problem is with FreeType ?

when i try to install the latest version im getting the error :

:KS
...<skipped>...
configure: creating ./config.status
config.status: creating unix-cc.mk
config.status: creating unix-def.mk
config.status: creating freetype-config
config.status: creating freetype2.pc
config.status: creating ftconfig.h
make: Nothing to be done for `unix'.

:KS
or for older version:

:KS
...<skipped>...
creating ft_conf.h
ft_conf.h is unchanged

:KS
So i tried a .rpm package

that gave me this error(using Kpackage tool or with konsole command):

rpm -U --replacepkgs  '///home/brecht/Desktop/freetype-static-2.3.4-1.fc7_90.cubbi2.x86_64.rpm';echo RESULT=$?
warning: ///home/brecht/Desktop/freetype-static-2.3.4-1.fc7_90.cubbi2.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 66534c2b
error: Failed dependencies:
	/sbin/ldconfig is needed by freetype-static-2.3.4-1.fc7_90.cubbi2.x86_64
RESULT=1

:KS

Could someone plz help me out on this one ?

---

### Post by testube_babies on 2007-08-31
Does this help?

[http://www.getdeb.net/release.php?id=1307](http://www.getdeb.net/release.php?id=1307)

Plus, all of the Pidgin dependencies should be in the repositories. 'sudo apt-get build-dep gaim' should install them.

---

### Post by Chiclette on 2007-08-31
thx very much, that helped me out.

---

