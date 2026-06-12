---
title: "Help compiling a file"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-06-01
I have installed [SCIM ]("http://www.scim-im.org/") with apt-get but it's not the latest version . I want to upgrade and tried dowloading the latest from their website. The readme file claims that I only need to 
```
./configure
make 
make install
```
'./configure' seems to work alright
but when i ran 'make' it just prints endless data and never stops
look:
```
sesho@ubuntu:/tmp/scim-1.2.3$ make
make  all-recursive
make[1]: Entering directory `/tmp/scim-1.2.3'
Making all in m4
make[2]: Entering directory `/tmp/scim-1.2.3/m4'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/scim-1.2.3/m4'
Making all in intl
make[2]: Entering directory `/tmp/scim-1.2.3/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/tmp/scim-1.2.3/intl'
Making all in src
make[2]: Entering directory `/tmp/scim-1.2.3/src'
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\"    -g -O2 -MT scim_backend.lo -MD -MP -MF ".deps/scim_backend.Tpo" -c -o scim_backend.lo scim_backend.cpp; \then mv -f ".deps/scim_backend.Tpo" ".deps/scim_backend.Plo"; else rm -f ".deps/scim_backend.Tpo"; exit 1; fi
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_backend.lo -MD -MP -MF .deps/scim_backend.Tpo -c scim_backend.cpp  -fPIC -DPIC -o .libs/scim_backend.o
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_backend.lo -MD -MP -MF .deps/scim_backend.Tpo -c scim_backend.cpp -o scim_backend.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\"    -g -O2 -MT scim_chartraits.lo -MD -MP -MF ".deps/scim_chartraits.Tpo" -c -o scim_chartraits.lo scim_chartraits.cpp; \
then mv -f ".deps/scim_chartraits.Tpo" ".deps/scim_chartraits.Plo"; else rm -f ".deps/scim_chartraits.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_chartraits.lo -MD -MP -MF .deps/scim_chartraits.Tpo -c scim_chartraits.cpp  -fPIC -DPIC -o .libs/scim_chartraits.o
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_chartraits.lo -MD -MP -MF .deps/scim_chartraits.Tpo -c scim_chartraits.cpp -o scim_chartraits.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\"    -g -O2 -MT scim_compose_key.lo -MD -MP -MF ".deps/scim_compose_key.Tpo" -c -o scim_compose_key.lo scim_compose_key.cpp; \
then mv -f ".deps/scim_compose_key.Tpo" ".deps/scim_compose_key.Plo"; else rm -f ".deps/scim_compose_key.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_compose_key.lo -MD -MP -MF .deps/scim_compose_key.Tpo -c scim_compose_key.cpp  -fPIC -DPIC -o .libs/scim_compose_key.o
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_compose_key.lo -MD -MP -MF .deps/scim_compose_key.Tpo -c scim_compose_key.cpp -o scim_compose_key.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\"    -g -O2 -MT scim_config_base.lo -MD -MP -MF ".deps/scim_config_base.Tpo" -c -o scim_config_base.lo scim_config_base.cpp; \
then mv -f ".deps/scim_config_base.Tpo" ".deps/scim_config_base.Plo"; else rm -f ".deps/scim_config_base.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_config_base.lo -MD -MP -MF .deps/scim_config_base.Tpo -c scim_config_base.cpp  -fPIC -DPIC -o .libs/scim_config_base.o
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_config_base.lo -MD -MP -MF .deps/scim_config_base.Tpo -c scim_config_base.cpp -o scim_config_base.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\"    -g -O2 -MT scim_config_module.lo -MD -MP -MF ".deps/scim_config_module.Tpo" -c -o scim_config_module.lo scim_config_module.cpp; \
then mv -f ".deps/scim_config_module.Tpo" ".deps/scim_config_module.Plo"; else rm -f ".deps/scim_config_module.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_config_module.lo -MD -MP -MF .deps/scim_config_module.Tpo -c scim_config_module.cpp  -fPIC -DPIC -o .libs/scim_config_module.o
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_config_module.lo -MD -MP -MF .deps/scim_config_module.Tpo -c scim_config_module.cpp -o scim_config_module.o >/dev/null 2>&1
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\"    -g -O2 -MT scim_connection.lo -MD -MP -MF ".deps/scim_connection.Tpo" -c -o scim_connection.lo scim_connection.cpp; \
then mv -f ".deps/scim_connection.Tpo" ".deps/scim_connection.Plo"; else rm -f ".deps/scim_connection.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_connection.lo -MD -MP -MF .deps/scim_connection.Tpo -c scim_connection.cpp  -fPIC -DPIC -o .libs/scim_connection.o
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_connection.lo -MD -MP -MF .deps/scim_connection.Tpo -c scim_connection.cpp -o scim_connection.o >/dev/null 2>&1
```


i tried with a different version of SCIM and got the same result
what can i do?

---

### Post by rdd on 2006-06-01
can you post the output you get from ./configure ?

---

### Post by seshomaru samma on 2006-06-01
this is ./configure's output:
```
sesho@ubuntu:/tmp/scim-1.2.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
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
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for ranlib... ranlib
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for signed... yes
checking for inline... inline
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for off_t... yes
checking for size_t... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for stdint.h... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for ptrdiff_t... yes
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
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... no
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration...
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for ranlib... (cached) ranlib
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
checking whether to build static libraries... yes
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
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking which extension is used for loadable modules... .so
checking which variable specifies run-time library path... LD_LIBRARY_PATH
checking for the default library search path... /lib /usr/lib
checking for objdir... .libs
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen in -ldl... (cached) yes
checking for dlerror... yes
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking for argz.h... (cached) yes
checking for error_t... yes
checking for argz_append... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking assert.h usability... yes
checking assert.h presence... yes
checking for assert.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for malloc.h... (cached) yes
checking for memory.h... (cached) yes
checking for stdlib.h... (cached) yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking for unistd.h... (cached) yes
checking dl.h usability... no
checking dl.h presence... no
checking for dl.h... no
checking sys/dl.h usability... no
checking sys/dl.h presence... no
checking for sys/dl.h... no
checking dld.h usability... no
checking dld.h presence... no
checking for dld.h... no
checking mach-o/dyld.h usability... no
checking mach-o/dyld.h presence... no
checking for mach-o/dyld.h... no
checking for string.h... (cached) yes
checking for strchr... yes
checking for strrchr... yes
checking for memcpy... yes
checking for memmove... yes
checking for strcmp... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for doxygen... no
checking for dot... NO
checking for dot... no
dirname: too few arguments
Try `dirname --help' for more information.
checking for perl... /usr/bin/perl
checking for xsltproc... /usr/bin/xsltproc
checking for /usr/share/sgml/docbook/xsl-stylesheets/html/tldp-html.xsl... no
checking for /usr/share/sgml/docbook/xsl-stylesheets/html/docbook.xsl... no
checking for /usr/share/xml/docbook/stylesheet/nwalsh/current/html/docbook.xsl... no
checking for intltool >= 0.33... 0.33 found
checking for perl... /usr/bin/perl
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking langinfo.h usability... yes
checking langinfo.h presence... yes
checking for langinfo.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for string.h... (cached) yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking hash_map usability... no
checking hash_map presence... no
checking for hash_map... no
checking ext/hash_map usability... yes
checking ext/hash_map presence... yes
checking for ext/hash_map... yes
checking for an ANSI C-conforming const... (cached) yes
checking for inline... (cached) inline
checking for size_t... (cached) yes
checking for char... yes
checking size of char... 1
checking for unsigned short int... yes
checking size of unsigned short int... 2
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long int... yes
checking size of unsigned long int... 4
checking for unsigned long long int... yes
checking size of unsigned long long int... 8
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for gettimeofday... yes
checking for memmove... (cached) yes
checking for memset... yes
checking for nl_langinfo... yes
checking for setlocale... (cached) yes
checking for daemon... yes
checking for opendir... (cached) yes
checking for closedir... (cached) yes
checking for readdir... (cached) yes
checking for usleep... yes
checking for nanosleep... yes
checking for gethostbyname... yes
checking for gethostbyname_r... yes
checking for socket... yes
checking for bind... yes
checking for accept... yes
checking for connect... yes
checking for listen... yes
checking for iconv... (cached) yes
checking for iconv declaration... (cached)
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0 pango >= 1.0.0 gdk-pixbuf-2.0 >= 2.0.0... checking for gthread-2.0 >= 2.0.0... checking for X... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating intl/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating src/scim_types.h
config.status: creating utils/Makefile
config.status: creating data/Makefile
config.status: creating data/icons/Makefile
config.status: creating data/pixmaps/Makefile
config.status: creating modules/Makefile
config.status: creating modules/FrontEnd/IMdkit/Makefile
config.status: creating modules/FrontEnd/Makefile
config.status: creating modules/IMEngine/Makefile
config.status: creating modules/Config/Makefile
config.status: creating modules/SetupUI/Makefile
config.status: creating docs/scim.cfg
config.status: creating docs/Makefile
config.status: creating docs/manual/Makefile
config.status: creating docs/manual/zh_CN/Makefile
config.status: creating docs/manual/zh_CN/figures/Makefile
config.status: creating configs/Makefile
config.status: creating extras/Makefile
config.status: creating extras/gtk2_immodule/Makefile
config.status: creating extras/setup/Makefile
config.status: creating extras/setup/scim-setup
config.status: creating extras/panel/Makefile
config.status: creating tests/Makefile
config.status: creating intltool-extract
config.status: creating intltool-merge
config.status: creating intltool-update
config.status: creating scim.pc
config.status: creating scim-gtkutils.pc
config.status: creating scim.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
config.status: executing intltool commands

Build options:
  Version                 1.2.3
  Install prefix          /usr/local
  Build shared libs       yes
  Build static libs       yes
  Enable debug            no
  Build tests/*           no

Module options:
  Simple config module    yes
  Socket config module    yes

  X11 FrontEnd module     no
  Socket FrontEnd module  yes

  RawCode IMEngine module yes
  Socket IMEngine module  yes

  GTK2 IMModule           no

  GUI Setup Utility       no

  GTK2 Panel GUI          no

  GTK2 Utility Library    no
  Enable TrayIcon         no

```

---

### Post by Ecthelion on 2006-06-01
> checking for g77... no
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

Maybe it'll help to install as many as you can of these... I've had same problem with other compilation and when it doesn't work, just install some of the 'no' and mostly it works.
Also it's always good to have g77 and fortran...
I wouldn't be surprised that's because they are missing that it doesn't work.

---

### Post by seshomaru samma on 2006-06-02
I installed g77 and fortran but no change
what can i do?

---

### Post by rdd on 2006-06-02
I am not an expert on shell scripting but this 

```
if /bin/sh ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\"    -g -O2 -MT scim_backend.lo -MD -MP -MF ".deps/scim_backend.Tpo" -c -o scim_backend.lo scim_backend.cpp; \then mv -f ".deps/scim_backend.Tpo" ".deps/scim_backend.Plo"; else rm -f ".deps/scim_backend.Tpo"; exit 1; fi
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_backend.lo -MD -MP -MF .deps/scim_backend.Tpo -c scim_backend.cpp  -fPIC -DPIC -o .libs/scim_backend.o
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I.. -I../src -I../intl -DSCIM_DATADIR=\"/usr/local/share/scim\" -DSCIM_LOCALEDIR=\"/usr/local/share/locale\" -DSCIM_SYSCONFDIR=\"/usr/local/etc\" -DSCIM_LIBEXECDIR=\"/usr/local/lib/scim-1.0\" -DSCIM_ICONDIR=\"/usr/local/share/scim/icons\" -DSCIM_MODULE_PATH=\"/usr/local/lib/scim-1.0\" -g -O2 -MT scim_backend.lo -MD -MP -MF .deps/scim_backend.Tpo -c scim_backend.cpp -o scim_backend.o >/dev/null 2>&1

```

looks like it is just echoing the script, not actually executing the commands. Maybe someone more familiar with this kind of stuff could comment. 

Also do you meet the 'Requirements' on this page for your version (sorry if that insults you, but sometimes I overlook these things) [http://www.scim-im.org/projects/skim]("http://www.scim-im.org/projects/skim")

The configure output doesn't seem to show anything critical so I am quite at a loss here. I'll do a test install later on, see what happens. Could you post what version exactly you downloaded and where.

Regards 

rdd

---

### Post by rdd on 2006-06-02
Oh the version thing. You are trying to compile scim 1.2.3 there. In the repos i find version 1.4.4-1ubuntu12

Do you need version 1.2.3 ?

---

### Post by seshomaru samma on 2006-06-02
[QUOTE=rdd]Oh the version thing. You are trying to compile scim 1.2.3 there. In the repos i find version 1.4.4-1ubuntu12

Do you need version 1.2.3 ?[/QUOTE]

```
sesho@ubuntu:~$ sudo apt-get install scim
Password:
Reading package lists... Done
Building dependency tree... Done
scim is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
sesho@ubuntu:~$ scim -version
Smart Common Input Method 1.0.2
```
where did you find the 1.4.4 version?
mine is a very old version and i want to upgrade

i downloaded it from [here ]("http://www.scim-im.org/downloads/scim_download")
i tried the latest version but since it didnt work i figured i'll try an early one but the results were the same

---

### Post by rdd on 2006-06-02
What version of Ubuntu are you on? It is in the normal dapper repos.

If in doubt, post your /etc/apt/sources.list

---

### Post by seshomaru samma on 2006-06-02
breezy!
i posted this before dapper came out
tonight i'll upgrade and hopefully enjoy a better SCIM
thanks for your help

---

