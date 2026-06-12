---
title: "error configuring something"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-11
I try to do ./configure and it tells me the configure could not be found.  I know it exists here is my terminal:

ryanzec@ryanzec-laptop:~/Desktop/xdebug-2.0.2/xdebug-2.0.2/debugclient$ ls -l
total 544
-rw-r--r-- 1 ryanzec ryanzec   1097 2007-11-11 11:17 acinclude.m4
drwxr-xr-x 2 ryanzec ryanzec   4096 2008-03-11 18:45 build
-rw-r--r-- 1 ryanzec ryanzec    102 2007-11-11 11:17 buildconf
-rw-r--r-- 1 ryanzec ryanzec  38504 2007-11-11 11:17 config.guess
-rw-r--r-- 1 ryanzec ryanzec   3084 2007-11-11 11:17 config.h.in
-rw-r--r-- 1 ryanzec ryanzec  28224 2007-11-11 11:17 config.sub
-rw-r--r-- 1 ryanzec ryanzec 237629 2007-11-11 11:17 configure
-rw-r--r-- 1 ryanzec ryanzec   4234 2007-11-11 11:17 configure.in
-rw-r--r-- 1 ryanzec ryanzec     43 2007-11-11 11:17 cvsclean
-rw-r--r-- 1 ryanzec ryanzec   4450 2007-11-11 11:17 debugclient.dsp
-rw-r--r-- 1 ryanzec ryanzec    319 2007-11-11 11:17 INSTALL
-rw-r--r-- 1 ryanzec ryanzec   5598 2007-11-11 11:17 install-sh
-rw-r--r-- 1 ryanzec ryanzec   3041 2007-11-11 11:17 LICENSE
-rw-r--r-- 1 ryanzec ryanzec 139118 2007-11-11 11:17 ltmain.sh
-rw-r--r-- 1 ryanzec ryanzec   8355 2007-11-11 11:17 main.c
-rw-r--r-- 1 ryanzec ryanzec  18358 2007-11-11 11:17 Makefile.in
-rw-r--r-- 1 ryanzec ryanzec      0 2007-11-11 11:17 missing
-rw-r--r-- 1 ryanzec ryanzec    668 2007-11-11 11:17 mkinstalldirs
-rw-r--r-- 1 ryanzec ryanzec   2826 2007-11-11 11:17 usefulstuff.c
-rw-r--r-- 1 ryanzec ryanzec   1523 2007-11-11 11:17 usefulstuff.h
ryanzec@ryanzec-laptop:~/Desktop/xdebug-2.0.2/xdebug-2.0.2/debugclient$ ./configure
bash: ./configure: Permission denied
ryanzec@ryanzec-laptop:~/Desktop/xdebug-2.0.2/xdebug-2.0.2/debugclient$ sudo ./configure
sudo: ./configure: command not found
ryanzec@ryanzec-laptop:~/Desktop/xdebug-2.0.2/xdebug-2.0.2/debugclient$

anyone know why i am getting this error?

---

### Post by gsiliceo on 2008-03-11
It seems that package has the wrong permissions, sometimes happens, you need to navigate to that folder using nautilus and right click the file, then properties/permissions, give it execute rights.
I forgot the command to do it faster.

---

