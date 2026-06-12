---
title: "Installing glsof errors"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by caljohnsmith on 2008-03-19
I was trying to install glsof (glsof.sourceforge.net), or a GUI for lsof, but ran into the following errors when I ran "sudo ./configure":

configure:1363: checking for a BSD-compatible install
configure:1418: result: /usr/bin/install -c
configure:1429: checking whether build environment is sane
configure:1472: result: yes
configure:1487: checking whether make sets $(MAKE)
configure:1507: result: yes
configure:1539: checking for working aclocal-1.4
configure:1550: result: missing
configure:1554: checking for working autoconf
configure:1565: result: missing
configure:1569: checking for working automake-1.4
configure:1580: result: missing
configure:1584: checking for working autoheader
configure:1595: result: missing
configure:1599: checking for working makeinfo
configure:1610: result: missing
configure:1663: checking for gcc
configure:1679: found /usr/bin/gcc
configure:1689: result: gcc
configure:1933: checking for C compiler version
configure:1936: gcc --version </dev/null >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.


I'm no programmer, so can someone give me a hand please? Thanks!

---

### Post by zerhacke on 2008-03-19
In a terminal, type 

sudo apt-get install build-essential

and hit enter.

---

### Post by caljohnsmith on 2008-03-19
> **zerhacke said:**
> In a terminal, type 

sudo apt-get install build-essential

and hit enter.

I did that, even rebooted, and still get the following errors:
=========================================
sudo ./configure

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLSOF... configure: error: Package requirements (
        glib-2.0        gtk+-2.0        libgnomeui-2.0  libglade-2.0    gconf-2.0
        ) were not met:

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLSOF_CFLAGS
and GLSOF_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
=================

Any ideas of what I should do now? :confused:

---

