---
title: "how do i get gmake?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by hc2995 on 2006-09-09
ok i downloaded a program that requires GNU make (IE gmake) BUT when i do "sudo apt-get install gmake or GNU make" i get nothing..... so does anyone know the sudo apt-get install for gmake?

---

### Post by hc2995 on 2006-09-09
bump

---

### Post by taurus on 2006-09-09
Have you tried compiling that source with make???

```
sudo aptitude install build-essential
```

---

### Post by hc2995 on 2006-09-09
did that but when i do gmake nothing (make works but gmake dosent and make dosent complie this application)

---

### Post by taurus on 2006-09-09
What application are you talking about?  Does either the README or INSTALl tell you to do something like

```

./configure
make
make install

```

---

### Post by hc2995 on 2006-09-09
its called Blitzed Open Proxy Monitor (BOPM) its and IRC open proxy monitor


google BOPM

---

### Post by skymt on 2006-09-09
gmake is another name for GNU make, which is the version pulled in by build-essential. It doesn't make any sense that it would ask for gmake and then not work with it.

---

### Post by taurus on 2006-09-09
What is the output of this command, in BOPM's directory after you unpack it then?

```
ls -la
```

---

### Post by hc2995 on 2006-09-09
ls -la:

howard@DELL:~$ cd ~/Desktop/bopm
howard@DELL:~/Desktop/bopm$ ls -la
total 1304
drwxr-xr-x 6 howard howard   4096 2006-09-09 06:10 .
drwxr-xr-x 9 howard howard   4096 2006-09-09 06:47 ..
-rw-r--r-- 1 howard howard 153604 2004-01-17 18:18 aclocal.m4
-rw-r--r-- 1 howard howard   4542 2004-01-17 18:18 acsite.m4
-rw-r--r-- 1 howard howard   6622 2004-01-17 18:18 bopm.conf.blitzed
-rw-r--r-- 1 howard howard  22759 2004-01-17 18:18 bopm.conf.sample
-rw-r--r-- 1 howard howard 121791 2004-01-17 18:18 ChangeLog
-rwxr-xr-x 1 howard howard  38504 2004-01-17 18:18 config.guess
-rw-r--r-- 1 howard howard  33777 2006-09-09 06:10 config.log
-rwxr-xr-x 1 howard howard  39019 2006-09-09 06:10 config.status
-rw-r--r-- 1 howard howard  28224 2004-01-17 18:18 config.sub
-rwxr-xr-x 1 howard howard 393018 2004-01-17 18:18 configure
-rw-r--r-- 1 howard howard   4695 2004-01-17 18:18 configure.in
drwxr-xr-x 6 howard howard   4096 2004-01-17 17:58 contrib
-rw-r--r-- 1 howard howard   2333 2004-01-17 18:18 CREDITS
drwxr-xr-x 2 howard howard   4096 2004-01-17 18:18 CVS
-rw-r--r-- 1 howard howard    138 2003-06-22 10:19 .cvsignore
-rwxr-xr-x 1 howard howard  12123 2004-01-17 18:18 depcomp
-rw-r--r-- 1 howard howard     23 2003-01-07 22:08 .gdbinit
-rw-r--r-- 1 howard howard   4526 2004-01-17 18:18 INSTALL
-rwxr-xr-x 1 howard howard   5598 2004-01-17 18:18 install-sh
-rwxr-xr-x 1 howard howard 150175 2006-09-09 06:10 libtool
-rw-r--r-- 1 howard howard  17982 2004-01-17 18:18 LICENSE
-rw-r--r-- 1 howard howard 141392 2004-01-17 18:18 ltmain.sh
-rw-r--r-- 1 howard howard  14762 2006-09-09 06:10 Makefile
-rw-r--r-- 1 howard howard    632 2004-01-17 18:18 Makefile.am
-rw-r--r-- 1 howard howard  14610 2004-01-17 18:18 Makefile.in
-rwxr-xr-x 1 howard howard  10270 2004-01-17 18:18 missing
-rwxr-xr-x 1 howard howard    722 2004-01-17 18:18 mkinstalldirs
drwxr-xr-x 3 howard howard   4096 2004-01-17 17:58 network-bopm
-rw-r--r-- 1 howard howard   6330 2004-01-17 18:18 README
drwxr-xr-x 5 howard howard   4096 2006-09-09 06:10 src
-rw-r--r-- 1 howard howard    101 2004-01-17 18:18 TODO
howard@DELL:~/Desktop/bopm$

---

### Post by hc2995 on 2006-09-09
./configure gives me this:

##############################################################################
Everything is now configured.  To compile libopm now, just type make.  It
requires GNU Make, which may be installed as gmake on your system.

libopm will be installed in /home/howard/bopm.  To change this, run:
   ./configure --prefix=DIRECTORY

##############################################################################

---

### Post by hc2995 on 2006-09-09
make give me this:

howard@DELL:~/Desktop/bopm$ make
Making all in src
make[1]: Entering directory `/home/howard/Desktop/bopm/src'
make  all-recursive
make[2]: Entering directory `/home/howard/Desktop/bopm/src'
Making all in libopm
make[3]: Entering directory `/home/howard/Desktop/bopm/src/libopm'
Making all in src
make[4]: Entering directory `/home/howard/Desktop/bopm/src/libopm/src'
make  all-am
make[5]: Entering directory `/home/howard/Desktop/bopm/src/libopm/src'
source='config.c' object='config.lo' libtool=yes \
        depfile='.deps/config.Plo' tmpdepfile='.deps/config.TPlo' \
        depmode=gcc3 /bin/sh ../depcomp \
        /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c -o config.lo `test -f 'config.c' || echo './'`config.c
rm -f .libs/config.lo
gcc -DHAVE_CONFIG_H -I. -I. -I. -g -O2 -c config.c -MT config.lo -MD -MP -MF .deps/config.TPlo  -fPIC -DPIC -o .libs/config.lo
config.c: In function 'libopm_config_create':
config.c:93: error: invalid lvalue in assignment
config.c:97: error: invalid lvalue in assignment
config.c:102: error: invalid lvalue in assignment
config.c: In function 'libopm_config_set':
config.c:191: error: invalid lvalue in assignment
make[5]: *** [config.lo] Error 1
make[5]: Leaving directory `/home/howard/Desktop/bopm/src/libopm/src'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/howard/Desktop/bopm/src/libopm/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/howard/Desktop/bopm/src/libopm'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/howard/Desktop/bopm/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/howard/Desktop/bopm/src'
make: *** [all-recursive] Error 1

---

### Post by taurus on 2006-09-09
So what happens if you run "make" now from a terminal?

---

### Post by skymt on 2006-09-10
It's not your fault. You have everything installed, and did everything right. There appears to be a bug in the program.

---

