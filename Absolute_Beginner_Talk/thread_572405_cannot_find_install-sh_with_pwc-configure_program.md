---
title: "cannot find install-sh with pwc-configure program"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Exonimus on 2007-10-10
Hello everyone,

I'm currently trying to install the pwc-config program. It's a program with a GUI to configure the settings of certain webcams(in my case, the pcvc680k) now, I'm kind of new to linux, but I've done some ./configure and make installs before. However, when I navigate to the map( cd '/home/roelof/Desktop/pwc-config') and afterwards, I try to run ./configure, it says
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
while the configure and install-sh files are really in the folder.. 

[http://img228.imageshack.us/img228/4134/schermafdrukyp5.png](http://img228.imageshack.us/img228/4134/schermafdrukyp5.png)

 I'm pretty sure it's something stupid I'm doing wrong :P help would be appreciated

for everyone's information, the install.txt included with the program says the following:
INSTALLATION:

First, as your normal user, type in the following:

->./configure<-
make

Once that finishes, the program will be installed into the src directory.
Alternatively, by logging in as 'root' you can install it into
/usr/local/bin/cam by typing:

make install

---

### Post by jfinkels on 2007-10-11
There's a 'pwc-source' package in the repositories. I suggest installing that package:```
sudo aptitude install pwc-source
``` which will automatically download the source file. You can view the readme by doing:```
less /usr/share/doc/pwc-source/README.Debian
```
One of the options it suggests for installing the drivers is to use module-assistant. You can install module-assistant by typing:```
sudo aptitude install module-assistant
``` and then following the instructions in the README, type:```
sudo module-assistant auto-install pwc-source
```

Let me know if this works for you.

---

### Post by Exonimus on 2007-10-11
the last command doesn't seem to work properly. the output is:

dh_testdir                                                                 
 &#9474; /usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules     
 &#9474; make[1]: Map '/usr/src/modules/pwc' wordt binnengegaan(=entering this folder)                     
 &#9474; dh_testdir                                                                 
 &#9474; make[1]: dh_testdir: Opdracht niet gevonden(didn't find assignment)                                
 &#9474; make[1]: *** [clean] Fout 127 (fout=error)                                             
 &#9474; make[1]: Map '/usr/src/modules/pwc' wordt verlaten(leaving folder  /usr/modules/pwc)                        
 &#9474; make: *** [kdist_build] Fout 2 (error 2)


also, the pwc-configure tool I spoke about in the first post is not the same as the pwc driver. it's a gui for various things. I think ubuntu has detected my webcam properly from the start(I can broadcast my webcam over e.g. msn) so that's not the problem, per se. sorry if it wasn't clear.

---

### Post by jfinkels on 2007-10-11
> **Exonimus said:**
> 
also, the pwc-configure tool I spoke about in the first post is not the same as the pwc driver. it's a gui for various things. I think ubuntu has detected my webcam properly from the start(I can broadcast my webcam over e.g. msn) so that's not the problem, per se. sorry if it wasn't clear.

Oooh, I'm sorry! Then forget what I said, and continue doing what you were doing. It looks like you may not have the appropriate permissions to access the install-sh file. What is the output of the following command in that directory?```
ls -l
```

---

### Post by Exonimus on 2007-10-13
sorry for the somewhat late reply :P
this is the output:
```

roelof@roelof-desktop:~/Desktop/pwc-config$ ls -l
-rw-rw-r-- 1 roelof roelof    142 2003-01-31 23:17 acconfig.h
-rw-rw-r-- 1 roelof roelof  48054 2003-01-31 23:18 aclocal.m4
-rw-rw-r-- 1 roelof roelof     38 2003-02-02 08:11 AUTHORS
-rw-rw-r-- 1 roelof roelof    203 2003-02-02 08:10 ChangeLog
-rw-rw-r-- 1 roelof roelof   4506 2003-01-31 23:18 config.h.in
-rw-r--r-- 1 roelof roelof   1635 2007-10-13 12:38 config.log
-rwxr-xr-x 1 roelof roelof 213057 2003-02-02 08:42 configure
-rw-r--r-- 1 roelof roelof    785 2003-02-02 07:56 configure.in
lrwxrwxrwx 1 roelof roelof     31 2007-10-10 17:44 COPYING -> /usr/share/automake-1.6/COPYING
lrwxrwxrwx 1 roelof roelof     31 2007-10-10 17:44 depcomp -> /usr/share/automake-1.6/depcomp
lrwxrwxrwx 1 roelof roelof     31 2007-10-10 17:44 INSTALL -> /usr/share/automake-1.6/INSTALL
lrwxrwxrwx 1 roelof roelof     34 2007-10-10 17:44 install-sh -> /usr/share/automake-1.6/install-sh
-rw-r--r-- 1 roelof roelof  14373 2003-02-02 08:00 Makefile.in
lrwxrwxrwx 1 roelof roelof     31 2007-10-10 17:44 missing -> /usr/share/automake-1.6/missing
lrwxrwxrwx 1 roelof roelof     37 2007-10-10 17:44 mkinstalldirs -> /usr/share/automake-1.6/mkinstalldirs
-rw-rw-r-- 1 roelof roelof     64 2003-02-02 08:12 NEWS
drwxrwxr-x 2 roelof roelof   4096 2003-02-02 08:02 po
-rw-rw-r-- 1 roelof roelof   1846 2003-02-04 01:28 README
drwxrwxr-x 3 roelof roelof   4096 2003-02-02 08:27 src
-rw-r--r-- 1 roelof roelof     65 2003-02-02 08:11 TODO


```

about the automake thing, that's one thing I've tried, so I think that's why it says automake-missing.. something

as far as my ubuntu knowledge goes, I think this is what you want to know:
```
lrwxrwxrwx 1 roelof roelof     31 2007-10-10 17:44 INSTALL -> /usr/share/automake-1.6/INSTALL
lrwxrwxrwx 1 roelof roelof     34 2007-10-10 17:44 install-sh -> /usr/share/automake-1.6/install-sh
```

also, I'm sorry if I do something stupid. It's just that I'm learning, and if I have a problem I go find possible solutions.. and if they dont help, I just try something else :)

also, when I try automake, I first do autoconf and aclocal, then type automake. it gives me this output: it says something is missing, so I tried the --add-missing option behind the command. As far as I know, it tries to guess stuff that's not there?
```
roelof@roelof-desktop:~/Desktop/pwc-config$ automake
configure.in:24: required file `./config.sub' not found
configure.in:24:   `automake --add-missing' can install `config.sub'
configure.in:4: required file `./missing' not found
configure.in:4:   `automake --add-missing' can install `missing'
configure.in:4: required file `./install-sh' not found
configure.in:4:   `automake --add-missing' can install `install-sh'
configure.in:24: required file `./config.guess' not found
configure.in:24:   `automake --add-missing' can install `config.guess'
src/Makefile.am: required file `./depcomp' not found
src/Makefile.am:   `automake --add-missing' can install `depcomp'
**roelof@roelof-desktop:~/Desktop/pwc-config$ automake --add-missing**
configure.in:24: installing `./config.sub'
configure.in:4: installing `./missing'
configure.in:4: installing `./install-sh'
configure.in:24: installing `./config.guess'
src/Makefile.am: installing `./depcomp'
roelof@roelof-desktop:~/Desktop/pwc-config$ automake
roelof@roelof-desktop:~/Desktop/pwc-config$ 
```

after this, I tried the ls-l command again. I think it gives a little other output
```
totaal 368
-rw-rw-r-- 1 roelof roelof    142 2003-01-31 23:17 acconfig.h
-rw-r--r-- 1 roelof roelof  52943 2007-10-13 12:47 aclocal.m4
-rw-rw-r-- 1 roelof roelof     38 2003-02-02 08:11 AUTHORS
drwxr-xr-x 2 roelof roelof   4096 2007-10-13 12:47 autom4te.cache
-rw-rw-r-- 1 roelof roelof    203 2003-02-02 08:10 ChangeLog
lrwxrwxrwx 1 roelof roelof     37 2007-10-13 12:47 config.guess -> /usr/share/automake-1.10/config.guess
-rw-rw-r-- 1 roelof roelof   4506 2003-01-31 23:18 config.h.in
-rw-r--r-- 1 roelof roelof   1635 2007-10-13 12:38 config.log
lrwxrwxrwx 1 roelof roelof     35 2007-10-13 12:47 config.sub -> /usr/share/automake-1.10/config.sub
-rwxr-xr-x 1 roelof roelof 243771 2007-10-13 12:47 configure
-rw-r--r-- 1 roelof roelof    785 2003-02-02 07:56 configure.in
lrwxrwxrwx 1 roelof roelof     31 2007-10-10 17:44 COPYING -> /usr/share/automake-1.6/COPYING
lrwxrwxrwx 1 roelof roelof     32 2007-10-13 12:47 depcomp -> /usr/share/automake-1.10/depcomp
lrwxrwxrwx 1 roelof roelof     31 2007-10-10 17:44 INSTALL -> /usr/share/automake-1.6/INSTALL
lrwxrwxrwx 1 roelof roelof     35 2007-10-13 12:47 install-sh -> /usr/share/automake-1.10/install-sh
-rw-r--r-- 1 roelof roelof  14373 2003-02-02 08:00 Makefile.in
lrwxrwxrwx 1 roelof roelof     32 2007-10-13 12:47 missing -> /usr/share/automake-1.10/missing
lrwxrwxrwx 1 roelof roelof     37 2007-10-10 17:44 mkinstalldirs -> /usr/share/automake-1.6/mkinstalldirs
-rw-rw-r-- 1 roelof roelof     64 2003-02-02 08:12 NEWS
drwxrwxr-x 2 roelof roelof   4096 2003-02-02 08:02 po
-rw-rw-r-- 1 roelof roelof   1846 2003-02-04 01:28 README
drwxrwxr-x 3 roelof roelof   4096 2007-10-13 12:49 src
-rw-r--r-- 1 roelof roelof     65 2003-02-02 08:11 TODO

```

---

### Post by jfinkels on 2007-10-13
Make sure you have automake-1.6 installed:```
sudo aptitude install automake1.6
```

Then try```
./configure
```
Then```
make
```
Then```
sudo make install
```
or instead of 'make install' install the checkinstall program:```
sudo aptitude install checkinstall
```
and do ```
sudo checkinstall
``` instead of 'sudo make install' (which I highly recommend doing).

If you get any errors doing ./configure or make or checkinstall, let me know!

---

### Post by Exonimus on 2007-10-13
I tried the ./configure and make before.. this is what I got

first, the ./configure. It was checking for all kinds of libraries, then, I got this(I didn't paste the complete list because everything that was above this went well) ```
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for msgfmt... no
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
roelof@roelof-desktop:~/Desktop/pwc-config$ 

```

so, two warnings, not sure if that's my problem..it says the config.h is unchanged, obviously, because I 've tried the command before..


now, after this, it's logical the make command went wrong:
```

roelof@roelof-desktop:~/Desktop/pwc-config$ make
make  all-recursive
make[1]: Map '/home/roelof/Desktop/pwc-config' wordt binnengegaan(entering folder)
Making all in src
make[2]: Map '/home/roelof/Desktop/pwc-config/src' wordt binnengegaan(entering folder)
Makefile:261: *** ontbrekend scheidingsteken.  Gestopt.(I think the correct translation would be: 'missing divider/seperating sign, stopped.'
make[2]: Map '/home/roelof/Desktop/pwc-config/src' wordt verlaten(exiting folder)
make[1]: *** [all-recursive] Fout 1(error 1)
make[1]: Map '/home/roelof/Desktop/pwc-config' wordt verlaten(leaving folder)
make: *** [all] Fout 2(error 2)
roelof@roelof-desktop:~/Desktop/pwc-config$ 

```

with the other command you specified, I got to choose some options.. didn't change anything though. but again, an error: ```
roelof@roelof-desktop:~/Desktop/pwc-config$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "config" does not
*** Warning: contain any digits. dpkg might not like that.

This package will be built according to these values: 

0 -  Maintainer: [ root@roelof-desktop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ pwc ]
3 -  Version: [ config ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ pwc-config ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Map '/home/roelof/Desktop/pwc-config/src' wordt binnengegaan
Makefile:261: *** ontbrekend scheidingsteken.  Gestopt.
make[1]: Map '/home/roelof/Desktop/pwc-config/src' wordt verlaten
make: *** [install-recursive] Fout 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

looks like the make and checkinstall command gave the same error... so it doesn't work yet..

also, thanks for the quick help so far, even if it hasn't solved my problem yet. I appreciate it :)

---

### Post by jfinkels on 2007-10-13
> **Exonimus said:**
> 
now, after this, it's logical the make command went wrong:
```

roelof@roelof-desktop:~/Desktop/pwc-config$ make
make  all-recursive
make[1]: Map '/home/roelof/Desktop/pwc-config' wordt binnengegaan(entering folder)
Making all in src
make[2]: Map '/home/roelof/Desktop/pwc-config/src' wordt binnengegaan(entering folder)
Makefile:261: *** ontbrekend scheidingsteken.  Gestopt.(I think the correct translation would be: 'missing divider/seperating sign, stopped.'
make[2]: Map '/home/roelof/Desktop/pwc-config/src' wordt verlaten(exiting folder)
make[1]: *** [all-recursive] Fout 1(error 1)
make[1]: Map '/home/roelof/Desktop/pwc-config' wordt verlaten(leaving folder)
make: *** [all] Fout 2(error 2)
roelof@roelof-desktop:~/Desktop/pwc-config$ 

```


You can't do checkinstall until you do make successfully.

It seems that the Makefile has an error in it. Can you post the output of this command:```
cat /home/roelof/Desktop/pwc-config/src/Makefile
```

---

### Post by Exonimus on 2007-10-13
oh my ... that's one hell of an output, I hope you know what you're looking for:

```
roelof@roelof-desktop:~$ cat /home/roelof/Desktop/pwc-config/src/Makefile
# Makefile.in generated by automake 1.10 from Makefile.am.
# src/Makefile.  Generated from Makefile.in by configure.

# Copyright (C) 1994, 1995, 1996, 1997, 1998, 1999, 2000, 2001, 2002,
# 2003, 2004, 2005, 2006  Free Software Foundation, Inc.
# This Makefile.in is free software; the Free Software Foundation
# gives unlimited permission to copy and/or distribute it,
# with or without modifications, as long as this notice is preserved.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY, to the extent permitted by law; without
# even the implied warranty of MERCHANTABILITY or FITNESS FOR A
# PARTICULAR PURPOSE.




pkgdatadir = $(datadir)/cam
pkglibdir = $(libdir)/cam
pkgincludedir = $(includedir)/cam
am__cd = CDPATH="$${ZSH_VERSION+.}$(PATH_SEPARATOR)" && cd
install_sh_DATA = $(install_sh) -c -m 644
install_sh_PROGRAM = $(install_sh) -c
install_sh_SCRIPT = $(install_sh) -c
INSTALL_HEADER = $(INSTALL_DATA)
transform = $(program_transform_name)
NORMAL_INSTALL = :
PRE_INSTALL = :
POST_INSTALL = :
NORMAL_UNINSTALL = :
PRE_UNINSTALL = :
POST_UNINSTALL = :
build_triplet = @build@
host_triplet = @host@
bin_PROGRAMS = cam$(EXEEXT)
subdir = src
DIST_COMMON = $(srcdir)/Makefile.am $(srcdir)/Makefile.in
ACLOCAL_M4 = $(top_srcdir)/aclocal.m4
am__aclocal_m4_deps = $(top_srcdir)/configure.in
am__configure_deps = $(am__aclocal_m4_deps) $(CONFIGURE_DEPENDENCIES) \
        $(ACLOCAL_M4)
mkinstalldirs = $(install_sh) -d
CONFIG_HEADER = $(top_builddir)/config.h
CONFIG_CLEAN_FILES =
am__installdirs = "$(DESTDIR)$(bindir)"
binPROGRAMS_INSTALL = $(INSTALL_PROGRAM)
PROGRAMS = $(bin_PROGRAMS)
am_cam_OBJECTS = main.$(OBJEXT) support.$(OBJEXT) interface.$(OBJEXT) \
        callbacks.$(OBJEXT)
cam_OBJECTS = $(am_cam_OBJECTS)
cam_DEPENDENCIES =
DEFAULT_INCLUDES = -I. -I$(top_builddir)@am__isrc@
depcomp = $(SHELL) $(top_srcdir)/depcomp
am__depfiles_maybe = depfiles
COMPILE = $(CC) $(DEFS) $(DEFAULT_INCLUDES) $(INCLUDES) $(AM_CPPFLAGS) \
        $(CPPFLAGS) $(AM_CFLAGS) $(CFLAGS)
CCLD = $(CC)
LINK = $(CCLD) $(AM_CFLAGS) $(CFLAGS) $(AM_LDFLAGS) $(LDFLAGS) -o $@
SOURCES = $(cam_SOURCES)
DIST_SOURCES = $(cam_SOURCES)
ETAGS = etags
CTAGS = ctags
DISTFILES = $(DIST_COMMON) $(DIST_SOURCES) $(TEXINFOS) $(EXTRA_DIST)
ACLOCAL = ${SHELL} /home/roelof/Desktop/pwc-config/missing --run aclocal-1.6
AMTAR = ${SHELL} /home/roelof/Desktop/pwc-config/missing --run tar
AUTOCONF = ${SHELL} /home/roelof/Desktop/pwc-config/missing --run autoconf
AUTOHEADER = ${SHELL} /home/roelof/Desktop/pwc-config/missing --run autoheader
AUTOMAKE = ${SHELL} /home/roelof/Desktop/pwc-config/missing --run automake-1.6
AWK = mawk
CATALOGS = 
CATOBJEXT = 
CC = gcc
CCDEPMODE = depmode=gcc3
CFLAGS = -g -O2 -Wall
CPP = gcc -E
CPPFLAGS = 
CYGPATH_W = @CYGPATH_W@
DATADIRNAME = 
DEFS = -DHAVE_CONFIG_H
DEPDIR = .deps
ECHO_C = 
ECHO_N = -n
ECHO_T = 
EGREP = /bin/grep -E
EXEEXT = 
GETTEXT_PACKAGE = cam
GMOFILES = 
GMSGFMT = 
GREP = /bin/grep
INSTALL = /usr/bin/install -c
INSTALL_DATA = ${INSTALL} -m 644
INSTALL_PROGRAM = ${INSTALL}
INSTALL_SCRIPT = ${INSTALL}
INSTALL_STRIP_PROGRAM = ${SHELL} $(install_sh) -c -s
INSTOBJEXT = 
INTLLIBS = 
LDFLAGS = 
LIBOBJS = 
LIBS = 
LTLIBOBJS = 
MAINT = #
MAKEINFO = ${SHELL} /home/roelof/Desktop/pwc-config/missing --run makeinfo
MKDIR_P = @MKDIR_P@
MKINSTALLDIRS = ./mkinstalldirs
MSGFMT = no
MSGFMT_OPTS = @MSGFMT_OPTS@
OBJEXT = o
PACKAGE = cam
PACKAGE_BUGREPORT = 
PACKAGE_CFLAGS = -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12  
PACKAGE_LIBS = -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
PACKAGE_NAME = 
PACKAGE_STRING = 
PACKAGE_TARNAME = 
PACKAGE_VERSION = 
PATH_SEPARATOR = :
PKG_CONFIG = /usr/bin/pkg-config
POFILES = 
POSUB = po
PO_IN_DATADIR_FALSE = @PO_IN_DATADIR_FALSE@
PO_IN_DATADIR_TRUE = @PO_IN_DATADIR_TRUE@
SET_MAKE = 
SHELL = /bin/bash
STRIP = 
USE_NLS = yes
VERSION = 0.1
XGETTEXT = :
abs_builddir = /home/roelof/Desktop/pwc-config/src
abs_srcdir = /home/roelof/Desktop/pwc-config/src
abs_top_builddir = /home/roelof/Desktop/pwc-config
abs_top_srcdir = /home/roelof/Desktop/pwc-config
ac_ct_CC = gcc
am__include = include
am__leading_dot = @am__leading_dot@
am__quote = 
am__tar = @am__tar@
am__untar = @am__untar@
bindir = ${exec_prefix}/bin
build = @build@
build_alias = 
build_cpu = @build_cpu@
build_os = @build_os@
build_vendor = @build_vendor@
builddir = .
datadir = ${datarootdir}
datarootdir = ${prefix}/share
docdir = ${datarootdir}/doc/${PACKAGE}
dvidir = ${docdir}
exec_prefix = ${prefix}
host = @host@
host_alias = 
host_cpu = @host_cpu@
host_os = @host_os@
host_vendor = @host_vendor@
htmldir = ${docdir}
includedir = ${prefix}/include
infodir = ${datarootdir}/info
install_sh = /home/roelof/Desktop/pwc-config/install-sh
libdir = ${exec_prefix}/lib
libexecdir = ${exec_prefix}/libexec
localedir = ${datarootdir}/locale
localstatedir = ${prefix}/var
mandir = ${datarootdir}/man
mkdir_p = @mkdir_p@
oldincludedir = /usr/include
pdfdir = ${docdir}
prefix = /usr/local
program_transform_name = s,x,x,
psdir = ${docdir}
sbindir = ${exec_prefix}/sbin
sharedstatedir = ${prefix}/com
srcdir = .
sysconfdir = ${prefix}/etc
target_alias = 
top_builddir = ..
top_srcdir = ..
INCLUDES = \
        -DPACKAGE_DATA_DIR=\""$(datadir)"\" \
        -DPACKAGE_LOCALE_DIR=\""$(prefix)/$(DATADIRNAME)/locale"\" \
        -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12  

cam_SOURCES = \
        main.c \
        support.c support.h \
        interface.c interface.h \
        callbacks.c callbacks.h

cam_LDADD = -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
all: all-am

.SUFFIXES:
.SUFFIXES: .c .o .obj
$(srcdir)/Makefile.in: # $(srcdir)/Makefile.am  $(am__configure_deps)
        @for dep in $?; do \
          case '$(am__configure_deps)' in \
            *$$dep*) \
              cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh \
                && exit 0; \
              exit 1;; \
          esac; \
        done; \
        echo ' cd $(top_srcdir) && $(AUTOMAKE) --gnu  src/Makefile'; \
        cd $(top_srcdir) && \
          $(AUTOMAKE) --gnu  src/Makefile
.PRECIOUS: Makefile
Makefile: $(srcdir)/Makefile.in $(top_builddir)/config.status
        @case '$?' in \
          *config.status*) \
            cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh;; \
          *) \
            echo ' cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@ $(am__depfiles_maybe)'; \
            cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@ $(am__depfiles_maybe);; \
        esac;

$(top_builddir)/config.status: $(top_srcdir)/configure $(CONFIG_STATUS_DEPENDENCIES)
        cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh

$(top_srcdir)/configure: # $(am__configure_deps)
        cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh
$(ACLOCAL_M4): # $(am__aclocal_m4_deps)
        cd $(top_builddir) && $(MAKE) $(AM_MAKEFLAGS) am--refresh
install-binPROGRAMS: $(bin_PROGRAMS)
        @$(NORMAL_INSTALL)
        test -z "$(bindir)" || $(MKDIR_P) "$(DESTDIR)$(bindir)"
        @list='$(bin_PROGRAMS)'; for p in $$list; do \
          p1=`echo $$p|sed 's/$(EXEEXT)$$//'`; \
          if test -f $$p \
          ; then \
            f=`echo "$$p1" | sed 's,^.*/,,;$(transform);s/$$/$(EXEEXT)/'`; \
           echo " $(INSTALL_PROGRAM_ENV) $(binPROGRAMS_INSTALL) '$$p' '$(DESTDIR)$(bindir)/$$f'"; \
           $(INSTALL_PROGRAM_ENV) $(binPROGRAMS_INSTALL) "$$p" "$(DESTDIR)$(bindir)/$$f" || exit 1; \
          else :; fi; \
        done

uninstall-binPROGRAMS:
        @$(NORMAL_UNINSTALL)
        @list='$(bin_PROGRAMS)'; for p in $$list; do \
          f=`echo "$$p" | sed 's,^.*/,,;s/$(EXEEXT)$$//;$(transform);s/$$/$(EXEEXT)/'`; \
          echo " rm -f '$(DESTDIR)$(bindir)/$$f'"; \
          rm -f "$(DESTDIR)$(bindir)/$$f"; \
        done

clean-binPROGRAMS:
        -test -z "$(bin_PROGRAMS)" || rm -f $(bin_PROGRAMS)
cam$(EXEEXT): $(cam_OBJECTS) $(cam_DEPENDENCIES) 
        @rm -f cam$(EXEEXT)
        $(LINK) $(cam_OBJECTS) $(cam_LDADD) $(LIBS)

mostlyclean-compile:
        -rm -f *.$(OBJEXT)

distclean-compile:
        -rm -f *.tab.c

include ./$(DEPDIR)/callbacks.Po
include ./$(DEPDIR)/interface.Po
include ./$(DEPDIR)/main.Po
include ./$(DEPDIR)/support.Po

.c.o:
@am__fastdepCC_TRUE@    $(COMPILE) -MT $@ -MD -MP -MF $(DEPDIR)/$*.Tpo -c -o $@ $<
@am__fastdepCC_TRUE@    mv -f $(DEPDIR)/$*.Tpo $(DEPDIR)/$*.Po
@am__fastdepCC_FALSE@   source='$<' object='$@' libtool=no \
@am__fastdepCC_FALSE@   DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
@am__fastdepCC_FALSE@   $(COMPILE) -c $<

.c.obj:
@am__fastdepCC_TRUE@    $(COMPILE) -MT $@ -MD -MP -MF $(DEPDIR)/$*.Tpo -c -o $@ `$(CYGPATH_W) '$<'`
@am__fastdepCC_TRUE@    mv -f $(DEPDIR)/$*.Tpo $(DEPDIR)/$*.Po
@am__fastdepCC_FALSE@   source='$<' object='$@' libtool=no \
@am__fastdepCC_FALSE@   DEPDIR=$(DEPDIR) $(CCDEPMODE) $(depcomp) \
@am__fastdepCC_FALSE@   $(COMPILE) -c `$(CYGPATH_W) '$<'`

ID: $(HEADERS) $(SOURCES) $(LISP) $(TAGS_FILES)
        list='$(SOURCES) $(HEADERS) $(LISP) $(TAGS_FILES)'; \
        unique=`for i in $$list; do \
            if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
          done | \
          $(AWK) '    { files[$$0] = 1; } \
               END { for (i in files) print i; }'`; \
        mkid -fID $$unique
tags: TAGS

TAGS:  $(HEADERS) $(SOURCES)  $(TAGS_DEPENDENCIES) \
                $(TAGS_FILES) $(LISP)
        tags=; \
        here=`pwd`; \
        list='$(SOURCES) $(HEADERS)  $(LISP) $(TAGS_FILES)'; \
        unique=`for i in $$list; do \
            if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
          done | \
          $(AWK) '    { files[$$0] = 1; } \
               END { for (i in files) print i; }'`; \
        if test -z "$(ETAGS_ARGS)$$tags$$unique"; then :; else \
          test -n "$$unique" || unique=$$empty_fix; \
          $(ETAGS) $(ETAGSFLAGS) $(AM_ETAGSFLAGS) $(ETAGS_ARGS) \
            $$tags $$unique; \
        fi
ctags: CTAGS
CTAGS:  $(HEADERS) $(SOURCES)  $(TAGS_DEPENDENCIES) \
                $(TAGS_FILES) $(LISP)
        tags=; \
        here=`pwd`; \
        list='$(SOURCES) $(HEADERS)  $(LISP) $(TAGS_FILES)'; \
        unique=`for i in $$list; do \
            if test -f "$$i"; then echo $$i; else echo $(srcdir)/$$i; fi; \
          done | \
          $(AWK) '    { files[$$0] = 1; } \
               END { for (i in files) print i; }'`; \
        test -z "$(CTAGS_ARGS)$$tags$$unique" \
          || $(CTAGS) $(CTAGSFLAGS) $(AM_CTAGSFLAGS) $(CTAGS_ARGS) \
             $$tags $$unique

GTAGS:
        here=`$(am__cd) $(top_builddir) && pwd` \
          && cd $(top_srcdir) \
          && gtags -i $(GTAGS_ARGS) $$here

distclean-tags:
        -rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags

distdir: $(DISTFILES)
        @srcdirstrip=`echo "$(srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
        topsrcdirstrip=`echo "$(top_srcdir)" | sed 's/[].[^$$\\*]/\\\\&/g'`; \
        list='$(DISTFILES)'; \
          dist_files=`for file in $$list; do echo $$file; done | \
          sed -e "s|^$$srcdirstrip/||;t" \
              -e "s|^$$topsrcdirstrip/|$(top_builddir)/|;t"`; \
        case $$dist_files in \
          */*) $(MKDIR_P) `echo "$$dist_files" | \
                           sed '/\//!d;s|^|$(distdir)/|;s,/[^/]*$$,,' | \
                           sort -u` ;; \
        esac; \
        for file in $$dist_files; do \
          if test -f $$file || test -d $$file; then d=.; else d=$(srcdir); fi; \
          if test -d $$d/$$file; then \
            dir=`echo "/$$file" | sed -e 's,/[^/]*$$,,'`; \
            if test -d $(srcdir)/$$file && test $$d != $(srcdir); then \
              cp -pR $(srcdir)/$$file $(distdir)$$dir || exit 1; \
            fi; \
            cp -pR $$d/$$file $(distdir)$$dir || exit 1; \
          else \
            test -f $(distdir)/$$file \
            || cp -p $$d/$$file $(distdir)/$$file \
            || exit 1; \
          fi; \
        done
check-am: all-am
check: check-am
all-am: Makefile $(PROGRAMS)
installdirs:
        for dir in "$(DESTDIR)$(bindir)"; do \
          test -z "$$dir" || $(MKDIR_P) "$$dir"; \
        done
install: install-am
install-exec: install-exec-am
install-data: install-data-am
uninstall: uninstall-am

install-am: all-am
        @$(MAKE) $(AM_MAKEFLAGS) install-exec-am install-data-am

installcheck: installcheck-am
install-strip:
        $(MAKE) $(AM_MAKEFLAGS) INSTALL_PROGRAM="$(INSTALL_STRIP_PROGRAM)" \
          install_sh_PROGRAM="$(INSTALL_STRIP_PROGRAM)" INSTALL_STRIP_FLAG=-s \
          `test -z '$(STRIP)' || \
            echo "INSTALL_PROGRAM_ENV=STRIPPROG='$(STRIP)'"` install
mostlyclean-generic:

clean-generic:

distclean-generic:
        -test -z "$(CONFIG_CLEAN_FILES)" || rm -f $(CONFIG_CLEAN_FILES)

maintainer-clean-generic:
        @echo "This command is intended for maintainers to use"
        @echo "it deletes files that may require special tools to rebuild."
clean: clean-am

clean-am: clean-binPROGRAMS clean-generic mostlyclean-am

distclean: distclean-am
        -rm -rf ./$(DEPDIR)
        -rm -f Makefile
distclean-am: clean-am distclean-compile distclean-generic \
        distclean-tags

dvi: dvi-am

dvi-am:

html: html-am

info: info-am

info-am:

install-data-am:

install-dvi: install-dvi-am

install-exec-am: install-binPROGRAMS

install-html: install-html-am

install-info: install-info-am

install-man:

install-pdf: install-pdf-am

install-ps: install-ps-am

installcheck-am:

maintainer-clean: maintainer-clean-am
        -rm -rf ./$(DEPDIR)
        -rm -f Makefile
maintainer-clean-am: distclean-am maintainer-clean-generic

mostlyclean: mostlyclean-am

mostlyclean-am: mostlyclean-compile mostlyclean-generic

pdf: pdf-am

pdf-am:

ps: ps-am

ps-am:

uninstall-am: uninstall-binPROGRAMS

.MAKE: install-am install-strip

.PHONY: CTAGS GTAGS all all-am check check-am clean clean-binPROGRAMS \
        clean-generic ctags distclean distclean-compile \
        distclean-generic distclean-tags distdir dvi dvi-am html \
        html-am info info-am install install-am install-binPROGRAMS \
        install-data install-data-am install-dvi install-dvi-am \
        install-exec install-exec-am install-html install-html-am \
        install-info install-info-am install-man install-pdf \
        install-pdf-am install-ps install-ps-am install-strip \
        installcheck installcheck-am installdirs maintainer-clean \
        maintainer-clean-generic mostlyclean mostlyclean-compile \
        mostlyclean-generic pdf pdf-am ps ps-am tags uninstall \
        uninstall-am uninstall-binPROGRAMS

# Tell versions [3.59,3.63) of GNU make to not export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:
roelof@roelof-desktop:~$ 

```

---

### Post by jfinkels on 2007-10-13
Well, apparently there is an error at line 261, but I don't really know how to fix that. Have you searched around for a .deb or .rpm package for this program? Or to double check and see if anyone else has had this problem? I don't really know how to help you here.

---

### Post by schorsch on 2007-10-13
If your system is Feisty Fawn and if it is up-to-date you have automake1.9 installed but pwc -config is looking for automake1.6 as it is ~4  years old.

```
sudo ln -s /usr/share/automake-1.9 /usr/share/automake-1.6
```
did the trick for me and I was able to compile the package without any errors.

---

### Post by Exonimus on 2007-10-13
bingo! after that command I tried autoconf,aclocal,automake,./configure,make again, and it worked. Now I just need to see how to launch that gui. thats not done by just entering pwc-config into the terminal as far as I know, but I dont have a clue how. Also, it said I don't have no necessarily run the make install part.. any advice?

---

### Post by schorsch on 2007-10-13
I installed the package via checkinstall using this commands:
```
./configure
make
sudo checkinstall
```
If you want to install it without building any package you will have to type
```
sudo make install
``` in the last step I mentioned. But I recommend to use the "checkinstall"-way as you will be able to remove the package in a proper way if you want to.

After that the tool should be available in /usr/local/bin and is called "cam". So typing
```
/usr/local/bin/cam
```
will start the tool. I do not own a webcam so I will not be able to support you furthermore when you get the tool running ... ;-)

---

### Post by Exonimus on 2007-10-14
hmm, I didn't need the make install command at all. After all the commands worked yesterday, (autoconf.aclocal,automake,./config,make)
I tried to just type in 'cam' in the /usr/src/modules/pwc folder.(since the readme said that was the default folder it'd be extracted/installed in)  and it worked! :D :D

If a mod wants, they can put a solved here.

thumbs up. you guys rock =)

---

### Post by jfinkels on 2007-10-14
> **Exonimus said:**
> hmm, I didn't need the make install command at all. After all the commands worked yesterday, (autoconf.aclocal,automake,./config,make)
I tried to just type in 'cam' in the /usr/src/modules/pwc folder.(since the readme said that was the default folder it'd be extracted/installed in)  and it worked! :D :D

If a mod wants, they can put a solved here.

thumbs up. you guys rock =)

I'm glad somebody knew how to help you!

The command 'make' will compile the program (i.e. convert it from source code to an executable form). The command 'make install' will install the executable file and any other relevant/necessary files across your system so that you don't have to be in the folder in which you compiled the program. The command 'checkinstall' will build a debian package (i.e. a .deb file) so that installation and removal of this program will be easy and portable in the future (i.e. you won't have to recompile from source again if you want to install the program on some other computer; it is highly recommended to do this though completely optional).

If you want, you can choose to edit your first post in this thread, select 'advanced', and then change the title yourself.

Let us know if you have any other questions!

---

### Post by Ghone on 2008-01-13
> **jfinkels said:**
> You can't do checkinstall until you do make successfully.

It seems that the Makefile has an error in it. Can you post the output of this command:```
cat /home/roelof/Desktop/pwc-config/src/Makefile
```

I believe that install-sh is a symlink to a file which does not exict in a directory which also does not exist.  I would do:```
 sudo mkdir /usr/share/automake-1.6
``` to create then ```
sudo gedit
``` to launch an editor to create a blank file and save it as ```
/usr/share/automake-1.6/install-sh
```

This should get you past the first error in the makefile and move you on to the next.

---

