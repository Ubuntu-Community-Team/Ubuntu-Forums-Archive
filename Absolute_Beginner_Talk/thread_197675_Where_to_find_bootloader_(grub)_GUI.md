---
title: "Where to find bootloader (grub) GUI"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Blinkiz on 2006-06-16
Hello
I would like to have a tool under gnome that can do many fancy stuff on the menu.lst file.

Where can I find a grub gui for gnome?
Also if I switch to KDE, what gui exist then?

I have tried to install grubconf without success (am a newbie you know) and I have found out that gnome-system-tools have a bootloader gui but I can't find it. Synaptic package manager says it's installed.

---

### Post by simone.brunozzi on 2006-06-16
Hi Blinkiz,
you can try grubconf:

[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)

Cheers,

---

### Post by Blinkiz on 2006-06-19
Okay, okay, why don't you help me then?

If I run sudo sh ./configure I get this text below.
```

loading cache ./config.cache
checking for non-GNU ld... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for strerror in -lcposix... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for Cygwin environment... no
checking for mingw32 environment... no
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... /bin/sed
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for object suffix... o
checking for executable suffix... no
checking command to parse /usr/bin/nm -B output... ok
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
checking for libgnomeui-2.0 gtk+-2.0...

```
How should I look to understand what is missing? Have tried to get makeinfo but I can't find it.

---

