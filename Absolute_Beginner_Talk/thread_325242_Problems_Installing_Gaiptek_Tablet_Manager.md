---
title: "Problems Installing Gaiptek Tablet Manager"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by scandalousartist on 2006-12-25
Het everyon. Has anyone had success getting the Gaiptek Tablet Manager installed on Ubuntu? I've been trying but Haven't had any luck yet.

So far I was able to configure the program from the directory but am unable to make the file once that is done. Here's what I've done so far -

root@dale:/home/dale/Desktop/Gaiptek# sh configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking dependency style of gcc... none
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... none
checking how to run the C++ preprocessor... g++ -E
configure: line 5975: AM_PROG_LIBTOOL: command not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTKMM... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating gaiptek.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

This makes the Make file

root@dale:/home/dale/Desktop/Gaiptek# make
make  all-recursive
make[1]: Entering directory `/home/dale/Desktop/Gaiptek'
Making all in src
make[2]: Entering directory `/home/dale/Desktop/Gaiptek/src'
Makefile:282: *** missing separator.  Stop.
make[2]: Leaving directory `/home/dale/Desktop/Gaiptek/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dale/Desktop/Gaiptek'
make: *** [all] Error 2

That's as far as I get. I'm not sure where the problem is. I've downloaded all the files from the snv sourceforge site and created the src folder with all the files in it in the Gaiptek Directory but not sure what to do from here. This whole terminal stuff is still new to me so I'm sure it's probably something real simple I'm overlooking but any help would be greatly appreciated. Thanks.

Dale

---

### Post by Regel on 2006-12-25
instead of using "make", try installing checkinstall and using it.
sudo apt-get install checkinstall 
#and then after configuring do
```
checkinstall
```it creates a .deb package, which can be installed easily and removed via synaptic.

---

### Post by scandalousartist on 2006-12-26
Thanks Regel for the tip. Unfortunately that didn't work either and still gave me the error when it tried to make file. I figured out where the problem was for the make file I was getting. Had to edit the aclocal.m4 file that was created in the same directory, had a space on line 282. Now when I run make file it gives me a different error -

root@dale:/home/dale/Desktop/Gaiptek# make
 cd . && /bin/sh /home/dale/Desktop/Gaiptek/missing --run automake-1.9 --gnu
cd . && /bin/sh /home/dale/Desktop/Gaiptek/missing --run autoconf
configure.in:16: error: possibly undefined macro: AM_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
make: *** [configure] Error 1

I tried running the m4_pattern_allow but it gave me a no rules error. Anyways, I found the line item in the error msg, it's in the configure.in file. Problem is I don't know how to correct this. Here's the code in the configure file -

# generated 2005/10/24 14:21:11 CDT by [email]bheadley@pharos.bheadley.org[/email].(none)
# using glademm V2.6.0

AC_PREREQ(2.50)
AC_INIT(gaiptek, 0.0,[bheadley@pharos.bheadley.org.(none)])
AM_INIT_AUTOMAKE
AC_CONFIG_HEADERS(config.h)

AC_ISC_POSIX
AC_PROG_CC
AM_PROG_CC_STDC
AC_HEADER_STDC
AC_PROG_CPP
AC_PROG_CXX
AC_PROG_CXXCPP
AM_PROG_LIBTOOL

AC_LANG_CPLUSPLUS

PKG_CHECK_MODULES(GTKMM,[gtkmm-2.4 >= 2.6.2],,
	[PKG_CHECK_MODULES(GTKMM,[gtkmm-2.4 >= 2.4.0])])
AC_SUBST(GTKMM_CFLAGS)
AC_SUBST(GTKMM_LIBS)

AC_OUTPUT(Makefile src/Makefile gaiptek.spec)

If anyone can help me figure this one out I would be forever grateful. Thanks.

Dale

---

### Post by wirah on 2008-01-06
Somebody have a hack around with this:

[http://debian.schmidham.net/old/gaiptek/](http://debian.schmidham.net/old/gaiptek/)

It has unsatisfiable dependencies, but if we can symlink those somewhat I think we may have a winner!

I don't have the tablet with me at present so I can't test this myself.

---

