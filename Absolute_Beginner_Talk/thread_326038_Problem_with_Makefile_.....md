---
title: "Problem with Makefile ...."
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by scandalousartist on 2006-12-26
Hey everyone. Anybody ever have a problem with undefined macros in a makefile. I'm trying to install Gaiptek Tablet Manager and I've been able to configure the file successfully but when I try to run the makefile it gives me a error -

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

### Post by tzulberti on 2006-12-27
> **scandalousartist said:**
> 
root@dale:/home/dale/Desktop/Gaiptek# make
cd . && /bin/sh /home/dale/Desktop/Gaiptek/missing --run automake-1.9 --gnu
cd . && /bin/sh /home/dale/Desktop/Gaiptek/missing --run autoconf


This could be the problem. You should install automake1.9 and autoconf...

---

