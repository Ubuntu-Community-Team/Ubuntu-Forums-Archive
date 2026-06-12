---
title: "help cant install freeciv"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-09-20
root@devil-laptop:/home/devil/Desktop/freeciv-2.1.0-beta6# ./configure --enable-client=sdl
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for gawk... (cached) gawk
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for ar... ar
checking for uname... uname
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for libcharset... no
checking for nl_langinfo and CODESET... yes
checking for strerror in -lcposix... no
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
checking whether we are using the GNU C Library 2.1 or newer... yes
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
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
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
checking for stpcpy... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for iconv... (cached) yes
checking for iconv declaration... (cached) 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... (cached) yes
checking for LC_MESSAGES... yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for GNU gettext in libc... yes
checking for dcgettext... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for bison... no
checking for catalogs to be installed...  ar cs ca da de el en_GB es et fa fi fr he hu it ja lt nl nb no pl pt pt_BR ro ru sv tr uk zh_CN
checking for ngettext in -lc... yes
checking whether libc's ngettext works at runtime... yes
checking for GNU xgettext version >= 0.10.36... yes
checking for GNU msgfmt version >= 0.10.35... yes
checking for C99 variadic macros... yes
checking for C99 variable arrays... yes
checking for C99 initializers... yes
checking for stdint.h... (cached) yes
checking for C99 stdint.h... yes
checking for gzgets in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for gzip... /bin/gzip
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.1.4... yes
checking for IMG_Load in -lSDL_image... yes
checking SDL/SDL_image.h usability... yes
checking SDL/SDL_image.h presence... yes
checking for SDL/SDL_image.h... yes
checking for freetype-config... no
checking for FreeType - version >= 2.1.3... no
*** The freetype-config script installed by FreeType 2 could not be found.
*** If FreeType 2 was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the FT2_CONFIG environment variable to the
*** full path to freetype-config.
configure: error: specified client 'sdl' not configurable (FreeType2 >= 2.1.3 is needed ([www.freetype.org](www.freetype.org)))
root@devil-laptop:/home/devil/Desktop/freeciv-2.1.0-beta6# apt-get install 
root@devil-laptop:/home/devil/Desktop/freeciv-2.1.0-beta6# FreeType2
-bash: FreeType2: command not found
root@devil-laptop:/home/devil/Desktop/freeciv-2.1.0-beta6# apt-get install FreeType2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package FreeType2

---

### Post by yabbadabbadont on 2007-09-20
Freeciv is already packaged and available in the official repositories.  Why are you trying to build it from source?

---

### Post by cosmoshell on 2007-09-20
diffrent version

---

### Post by afonic on 2007-09-20
The error message is pretty obvious. Install freetype. (the dev package too)

---

### Post by yabbadabbadont on 2007-09-20
```
sudo apt-get build-dep freeciv
```

;)

---

### Post by cosmoshell on 2007-09-20
what is build-dep

---

### Post by yabbadabbadont on 2007-09-20
"build dependencies"

Read the "apt-get" man page for details.  :)

---

