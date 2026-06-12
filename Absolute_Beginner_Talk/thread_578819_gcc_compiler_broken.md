---
title: "gcc compiler broken"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Jive Turkey on 2007-10-17
So I had to rebuild this thing agian because...I dunno why it broke, but the .deb from the repos comes with hbci and ofx disabled which makes it no more useful than a spreadsheet IMHO.

Anyway, I know the gcc worked correctly 30 min ago and the only thing I did since then was run:
```
sudo apt-get -d source gnucash

```

I'm building/have built this later version from the gnucash website and when I run ./configure this happens (it worked 30 min ago and not now):

```
ck@skynet:~/Desktop/gnucash-2.2.1$ ./configure --enable-hbci --enable-ofx
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
ck@skynet:~/Desktop/gnucash-2.2.1$ 
```

this is in the config.log:
```
  $ ./configure --enable-hbci --enable-ofx

## --------- ##
## Platform. ##
## --------- ##

hostname = skynet
uname -m = i686
uname -r = 2.6.20-16-generic
uname -s = Linux
uname -v = #2 SMP Sun Sep 23 19:50:39 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2202: checking for a BSD-compatible install
configure:2258: result: /usr/bin/install -c
configure:2269: checking whether build environment is sane
configure:2312: result: yes
configure:2340: checking for a thread-safe mkdir -p
configure:2379: result: /bin/mkdir -p
configure:2392: checking for gawk
configure:2408: found /usr/bin/gawk
configure:2419: result: gawk
configure:2430: checking whether make sets $(MAKE)
configure:2451: result: yes
configure:2707: checking for gcc
configure:2723: found /usr/bin/gcc
configure:2734: result: gcc
configure:2972: checking for C compiler version
configure:2979: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2982: $? = 0
configure:2989: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2992: $? = 0
configure:2999: gcc -V >&5
gcc: '-V' option must have argument
configure:3002: $? = 1
configure:3025: checking for C compiler default output file name
configure:3052: gcc    conftest.c  >&5
gcc: error trying to exec 'cc1': execvp: No such file or directory
configure:3055: $? = 1
configure:3093: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "gnucash"
| #define PACKAGE_TARNAME "gnucash"
| #define PACKAGE_VERSION "2.2.1"
| #define PACKAGE_STRING "gnucash 2.2.1"
| #define PACKAGE_BUGREPORT "gnucash-devel@gnucash.org"
| #define PACKAGE "gnucash"
| #define VERSION "2.2.1"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:3100: error: C compiler cannot create executables
See `config.log' for more details.
```

---

### Post by taurus on 2007-10-17
Try installing the build-essential package first before you run ./configure again.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Jive Turkey on 2007-10-17
I think I fugured it out,
I used sudo when I shouldn't have either when building or installing the package from source or configuring the source and overwrote some key components of gnome.  No worries, its easy to reinstall [sigh].

---

### Post by gummo on 2007-10-20
Thanx taurus, this did it for me: 

[quote=taurus]
Try installing the build-essential package first before you run ./configure again.

Code:

sudo aptitude update
sudo aptitude install build-essential
[/quote]

---

