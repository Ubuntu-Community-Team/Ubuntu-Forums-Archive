---
title: "conky installation problem"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by vamsibethapudy on 2008-02-19
> vamsi@vamsi-laptop:~/Programs/conky-1.4.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
vamsi@vamsi-laptop:~/Programs/conky-1.4.9$ sudo apt-get install gcc
[sudo] password for vamsi:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
The following packages were automatically installed and are no longer required:
  libsvga1 libglide2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
vamsi@vamsi-laptop:~/Programs/conky-1.4.9$ 

this is what i get when i tried installing conky got from sourcefourge
& this is part of the config.log that is relevant
> 
configure:2604: checking for gcc
configure:2620: found /usr/bin/gcc
configure:2631: result: gcc
configure:2869: checking for C compiler version
configure:2876: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2879: $? = 0
configure:2886: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2889: $? = 0
configure:2896: gcc -V >&5
gcc: '-V' option must have argument
configure:2899: $? = 1
configure:2922: checking for C compiler default output file name
configure:2949: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2952: $? = 1
configure:2990: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "Conky"
| #define PACKAGE_TARNAME "conky"
| #define PACKAGE_VERSION "1.4.9"
| #define PACKAGE_STRING "Conky 1.4.9"
| #define PACKAGE_BUGREPORT "brenden1@users.sourceforge.net"
| #define PACKAGE "conky"
| #define VERSION "1.4.9"
| /* end confdefs.h.  */


---

### Post by spiderbatdad on 2008-02-19
what do you get if you open a terminal and enter ```
sudo apt-get install conky
```?

or you could install build-essential to compile that package...also in synaptic.

---

### Post by vamsibethapudy on 2008-02-19
thanks.
got the problem solved.
i changed the software source to another server & apt-get did the trick.
but it still a mystery why i got an error in the previous installation.
does anyone know??:confused:

---

### Post by spiderbatdad on 2008-02-19
you needed build-essential

---

