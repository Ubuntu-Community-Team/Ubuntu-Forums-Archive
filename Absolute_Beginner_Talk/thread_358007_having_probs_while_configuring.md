---
title: "having probs while configuring"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by yasasvy on 2007-02-10
**hi! .. i was trying to install gtypist.. but couldnt quite finish it .. i have installed all the dependencies including ncurses.. but.. it shows . something else.. wht could be the prob?? and the "make" command isnt working.. it says.. no targets.. soo i tried which make!! whts the difference b/w those two commands???**




nanyam@home:~$ su
Password:
root@home:/home/nanyam# cd /home/nanyam/Desktop/
root@home:/home/nanyam/Desktop# tar zxvf /home/nanyam/Desktop/gtypist-2.7.tar.gz
gtypist-2.7/
gtypist-2.7/intl/
gtypist-2.7/intl/ChangeLog
gtypist-2.7/intl/Makefile.in
gtypist-2.7/intl/config.charset
gtypist-2.7/intl/locale.alias
gtypist-2.7/intl/ref-add.sin
gtypist-2.7/intl/ref-del.sin
gtypist-2.7/intl/gmo.h
gtypist-2.7/intl/gettextP.h
gtypist-2.7/intl/hash-string.h
gtypist-2.7/intl/loadinfo.h
gtypist-2.7/intl/plural-exp.h
gtypist-2.7/intl/eval-plural.h
gtypist-2.7/intl/localcharset.h
gtypist-2.7/intl/relocatable.h
gtypist-2.7/intl/os2compat.h
gtypist-2.7/intl/libgnuintl.h.in
gtypist-2.7/intl/bindtextdom.c
gtypist-2.7/intl/dcgettext.c
gtypist-2.7/intl/dgettext.c
gtypist-2.7/intl/gettext.c
gtypist-2.7/intl/finddomain.c
gtypist-2.7/intl/loadmsgcat.c
gtypist-2.7/intl/localealias.c
gtypist-2.7/intl/textdomain.c
gtypist-2.7/intl/l10nflist.c
gtypist-2.7/intl/explodename.c
gtypist-2.7/intl/dcigettext.c
gtypist-2.7/intl/dcngettext.c
gtypist-2.7/intl/dngettext.c
gtypist-2.7/intl/ngettext.c
gtypist-2.7/intl/plural.y
gtypist-2.7/intl/plural-exp.c
gtypist-2.7/intl/localcharset.c
gtypist-2.7/intl/relocatable.c
gtypist-2.7/intl/localename.c
gtypist-2.7/intl/log.c
gtypist-2.7/intl/osdep.c
gtypist-2.7/intl/os2compat.c
gtypist-2.7/intl/intl-compat.c
gtypist-2.7/intl/plural.c
gtypist-2.7/intl/VERSION
gtypist-2.7/po/
gtypist-2.7/po/Makefile.in.in
gtypist-2.7/po/remove-potcdate.sin
gtypist-2.7/po/quot.sed
gtypist-2.7/po/boldquot.sed
gtypist-2.7/po/en@quot.header
gtypist-2.7/po/en@boldquot.header
gtypist-2.7/po/insert-header.sin
gtypist-2.7/po/Rules-quot
gtypist-2.7/po/Makevars
gtypist-2.7/po/POTFILES.in
gtypist-2.7/po/gtypist.pot
gtypist-2.7/po/stamp-po
gtypist-2.7/po/de.po
gtypist-2.7/po/cs.po
gtypist-2.7/po/es.po
gtypist-2.7/po/fi.po
gtypist-2.7/po/fr.po
gtypist-2.7/po/ru.po
gtypist-2.7/po/zh_TW.po
gtypist-2.7/po/de.gmo
gtypist-2.7/po/cs.gmo
gtypist-2.7/po/es.gmo
gtypist-2.7/po/fi.gmo
gtypist-2.7/po/fr.gmo
gtypist-2.7/po/ru.gmo
gtypist-2.7/po/zh_TW.gmo
gtypist-2.7/README
gtypist-2.7/Makefile.in
gtypist-2.7/configure
gtypist-2.7/ABOUT-NLS
gtypist-2.7/AUTHORS
gtypist-2.7/COPYING
gtypist-2.7/ChangeLog
gtypist-2.7/INSTALL
gtypist-2.7/Makefile.am
gtypist-2.7/NEWS
gtypist-2.7/THANKS
gtypist-2.7/TODO
gtypist-2.7/aclocal.m4
gtypist-2.7/config.guess
gtypist-2.7/config.h.in
gtypist-2.7/config.rpath
gtypist-2.7/config.sub
gtypist-2.7/configure.in
gtypist-2.7/depcomp
gtypist-2.7/elisp-comp
gtypist-2.7/install-sh
gtypist-2.7/missing
gtypist-2.7/mkinstalldirs
gtypist-2.7/gtypist.c
gtypist-2.7/cursmenu.c
gtypist-2.7/script.c
gtypist-2.7/error.c
gtypist-2.7/getopt.c
gtypist-2.7/getopt1.c
gtypist-2.7/cursmenu.h
gtypist-2.7/error.h
gtypist-2.7/getopt.h
gtypist-2.7/gettext.h
gtypist-2.7/gtypist.h
gtypist-2.7/script.h
gtypist-2.7/typefortune
gtypist-2.7/gtypist.1
gtypist-2.7/typefortune.1
gtypist-2.7/configur.bat
gtypist-2.7/version.sh
gtypist-2.7/configur.bat.in
gtypist-2.7/autogen.sh
gtypist-2.7/INSTALL.in
gtypist-2.7/QUESTIONS
gtypist-2.7/m4/
gtypist-2.7/m4/Makefile.in
gtypist-2.7/m4/Makefile.am
gtypist-2.7/m4/codeset.m4
gtypist-2.7/m4/gettext.m4
gtypist-2.7/m4/glibc21.m4
gtypist-2.7/m4/iconv.m4
gtypist-2.7/m4/intdiv0.m4
gtypist-2.7/m4/inttypes.m4
gtypist-2.7/m4/inttypes_h.m4
gtypist-2.7/m4/inttypes-pri.m4
gtypist-2.7/m4/isc-posix.m4
gtypist-2.7/m4/lcmessage.m4
gtypist-2.7/m4/lib-ld.m4
gtypist-2.7/m4/lib-link.m4
gtypist-2.7/m4/lib-prefix.m4
gtypist-2.7/m4/nls.m4
gtypist-2.7/m4/po.m4
gtypist-2.7/m4/progtest.m4
gtypist-2.7/m4/stdint_h.m4
gtypist-2.7/m4/uintmax_t.m4
gtypist-2.7/m4/ulonglong.m4
gtypist-2.7/lessons/
gtypist-2.7/lessons/Makefile.in
gtypist-2.7/lessons/ChangeLog
gtypist-2.7/lessons/Makefile.am
gtypist-2.7/lessons/gtypist.typ
gtypist-2.7/lessons/d.typ
gtypist-2.7/lessons/demo.typ
gtypist-2.7/lessons/esp.typ
gtypist-2.7/lessons/cs.typ
gtypist-2.7/lessons/ru.typ
gtypist-2.7/lessons/m.typ
gtypist-2.7/lessons/n.typ
gtypist-2.7/lessons/q.typ
gtypist-2.7/lessons/r.typ
gtypist-2.7/lessons/s.typ
gtypist-2.7/lessons/t.typ
gtypist-2.7/lessons/u.typ
gtypist-2.7/lessons/v.typ
gtypist-2.7/lessons/ttde.typ
gtypist-2.7/lessons/ktde.typ
gtypist-2.7/lessons/ktdk2.typ
gtypist-2.7/lessons/kten.typ
gtypist-2.7/lessons/ktfr2.typ
gtypist-2.7/lessons/ktnumber.typ
gtypist-2.7/lessons/ktdk.typ
gtypist-2.7/lessons/ktdvorak.typ
gtypist-2.7/lessons/ktfr.typ
gtypist-2.7/lessons/ktno.typ
gtypist-2.7/tools/
gtypist-2.7/tools/Makefile.in
gtypist-2.7/tools/Makefile.am
gtypist-2.7/tools/typcombine
gtypist-2.7/tools/typv1tov2
gtypist-2.7/tools/ktouch2typ.pl
gtypist-2.7/tools/gtypist.pm
gtypist-2.7/tools/tt2typ.pl
gtypist-2.7/tools/gtypist-mode.el
gtypist-2.7/tools/findwords
gtypist-2.7/doc/
gtypist-2.7/doc/gpl.texi
gtypist-2.7/doc/fdl.texi
gtypist-2.7/doc/Makefile.in
gtypist-2.7/doc/ChangeLog
gtypist-2.7/doc/Makefile.am
gtypist-2.7/doc/mdate-sh
gtypist-2.7/doc/stamp-1
gtypist-2.7/doc/stamp-vti
gtypist-2.7/doc/texinfo.tex
gtypist-2.7/doc/version.texi
gtypist-2.7/doc/gtypist.texi
gtypist-2.7/doc/gtypist.cs.texi
gtypist-2.7/doc/gtypist.html
gtypist-2.7/doc/gtypist.cs.html
gtypist-2.7/doc/gtypist.info
root@home:/home/nanyam/Desktop# ./configure
bash: ./configure: No such file or directory
root@home:/home/nanyam/Desktop# cd gtypist-2.7
root@home:/home/nanyam/Desktop/gtypist-2.7# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) gawk
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for bison... bison -y
checking for wbkgdset in -lcurses... no
checking for wbkgdset in -lncurses... no
*** The curses or ncurses library is required!
root@home:/home/nanyam/Desktop/gtypist-2.7# which make
/usr/bin/make
root@home:/home/nanyam/Desktop/gtypist-2.7# which make install
/usr/bin/make
/usr/bin/install
root@home:/home/nanyam/Desktop/gtypist-2.7# checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ nanyam@home ]
1 -  Summary: [ typing tutor ]
2 -  Name:    [ gtypist ]
3 -  Version: [ 2.7 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gtypist-2.7 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by taurus on 2007-02-10
If there is an error to ./configure, no need to go further because it's not going to work.  Therefore, you need to install both curses and ncurses to fix the problem first.

```
sudo aptitude update
sudo aptitude install curses ncurses
```
Then, run your ./configure again.

---

### Post by yasasvy on 2007-02-10
thnx for the reply.. :) but i already installed both those curses.. but i  still have prob! :(

---

### Post by taurus on 2007-02-10
Did you at least try to reboot after you install curses or ncurses?

---

### Post by yasasvy on 2007-02-10
yeah i did that .. twice to be frank!

---

### Post by yasasvy on 2007-02-10
any possible solutions for this problm?? i need that software... atleast can anybody a good application to learn typing??

---

