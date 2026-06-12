---
title: "Can't compile the Mirage engine"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by uruahv on 2006-11-22
Hey!

I got problems with compiling a theme engine found at [http://www.gnome-look.org/content/show.php?content=43793](http://www.gnome-look.org/content/show.php?content=43793) .

This is what I get:

```
uruahv@ubuntu:~/Desktop/mirage-engine-0.1$ ./autogen.sh --prefix=/usr
aclocal:configure.ac:15: warning: macro `AM_DISABLE_STATIC' not found in library
aclocal:configure.ac:17: warning: macro `AM_PROG_LIBTOOL' not found in library
configure.ac:15: error: possibly undefined macro: AM_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:16: error: possibly undefined macro: AC_LIBTOOL_WIN32_DLL
configure.ac:17: error: possibly undefined macro: AM_PROG_LIBTOOL
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
engine/Makefile.am:4: Libtool library used but `LIBTOOL' is undefined
engine/Makefile.am:4: 
engine/Makefile.am:4: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
engine/Makefile.am:4: to `configure.ac' and run `aclocal' and `autoconf' again.
engine/Makefile.am: installing `./depcomp'
Makefile.am: installing `./INSTALL'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
./configure: line 4324: AM_DISABLE_STATIC: command not found
./configure: line 4325: AC_LIBTOOL_WIN32_DLL: command not found
./configure: line 4326: AM_PROG_LIBTOOL: command not found
./configure: line 4331: syntax error near unexpected token `GTK,'
./configure: line 4331: `PKG_CHECK_MODULES(GTK, gtk+-2.0 >= 2.7.0,,'

Now type 'make' to compile themes
uruahv@ubuntu:~/Desktop/mirage-engine-0.1$ make
make: *** No targets specified and no makefile found. Stop.
```I have both Ubuntulooks and Murrine engine installed, the author sais they are needed.

And when I look at the comments at gnome-look, I see that everyone else got the engine installed, so the problem is probably in me. Can anyone help me with this?

---

