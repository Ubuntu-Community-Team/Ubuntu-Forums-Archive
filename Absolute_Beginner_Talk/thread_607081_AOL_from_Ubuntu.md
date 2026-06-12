---
title: "AOL from Ubuntu"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by dtleigh on 2007-11-08
So, I've successfully installed 7.04 and am dualbooting with Windows XP.
I intend ditching XP just as soon as I can get an internet connection through my service provider, AOL, using Ubuntu/Firefox.

I'm following the AOL and Linux tutorial from yolinux.com...
1) Downloaded peng1.0a01.tar.gz 
2) Executed....
    # tar xzf peng1.0a01.tar.gz
    # cd peng
    # ./recompile      
....and got this output.....

loading cache ./config.cache
checking host system type... i386-pc-none
checking target system type... i386-pc-none
checking build system type... i386-pc-none
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for a C-Compiler... 
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

Now, getting into dualbooting was taxing enough...where do I go from here?

:(:(:(

---

### Post by Maestro23 on 2007-11-08
Install build-essential first.

> sudo apt-get install build-essential

If you get more errors after installing that, post back.

---

### Post by dtleigh on 2007-11-10
Yep! Still getting errors, but different ones after successfully installing build-essential (using Synaptic Package Manager bundled with Ubuntu 7.04 distro).

Here is the output - we can see that the C compiler is OK, but.....

peng# ./recompile
Wavplay exist , ok
rm: cannot remove `configure': No such file or directory
loading cache ./config.cache
checking host system type... i386-pc-none
checking target system type... i386-pc-none
checking build system type... i386-pc-none
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for a C-Compiler... 
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for a C++-Compiler... 
checking for g++... (cached) g++
checking whether the C++ compiler (g++ -D_REENTRANT -s) works... yes
checking whether the C++ compiler (g++ -D_REENTRANT -s) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether g++ supports -fexceptions... (cached) yes
checking whether g++ supports -frtti... (cached) yes
checking how to run the C++ preprocessor... (cached) g++ -E
checking whether g++ supports -frepo... (cached) yes
checking for Cygwin environment... (cached) no
checking for mingw32 environment... (cached) no
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for /usr/bin/ld option to reload object files... (cached) -r
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking how to recognise dependant libraries... (cached) pass_all
checking for object suffix... (cached) o
checking for executable suffix... (cached) no
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
updating cache ./config.cache
loading cache ./config.cache within ltconfig
checking for objdir... .libs
checking for g++ option to produce PIC... (cached)  -fPIC
checking if g++ PIC flag  -fPIC works... (cached) yes
checking if g++ static flag -static works... (cached) yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.lo... yes
checking if g++ supports -fno-rtti -fno-exceptions ... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... no
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... no
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for dlfcn.h... (cached) yes
checking whether a program can dlopen itself... (cached) no
creating libtool
loading cache ./config.cache
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... (cached) no
checking for extra includes... no
checking for extra libs... no
creating ./config.status
creating Makefile
creating peng/Makefile
creating config.h
Making clean in .
make[1]: Entering directory `/peng'
make[1]: Nothing to be done for `clean-am'.
make[1]: Leaving directory `/peng'
Making clean in peng
make[1]: Entering directory `/peng/peng'
test -z "peng" || rm -f peng
rm -rf .libs _libs
rm -f *.o core *.core
rm -f *.o
rm -f *.lo
make[1]: Leaving directory `/peng/peng'

PengAol V1.0 By Guth Stephane (birdy57)
---------------------------------------

In this version you can conditinal compilation making
(May not compile all drivers that you don't need)

Do you want to actived this option ?
answer by (y or n)
y
Conditional compilation
Do you want to use the modem driver ? (y/n)
y
Do you want to use the Cable driver ? (y/n)
y
Do you want to use the Ppp driver ? (y/n)
y
Do you want to use the TunTap driver ? (y/n)
y
Do you want to use the Debug ? (y/n)
Warning ! that can slow down the connection
n
make  all-recursive
make[1]: Entering directory `/peng'
Making all in peng
make[2]: Entering directory `/peng/peng'
g++ -DHAVE_CONFIG_H -I. -I. -I..     -D_REENTRANT -c threadELV3.cpp
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/iostream.h:31,
                 from cclienttoaol30.h:26,
                 from kernel30.h:47,
                 from caolcmd30.h:21,
                 from threadELV3.h:24,
                 from threadELV3.cpp:21:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
kernel30.h:152: error: ISO C++ forbids declaration of â€˜CAolCmd30â€™ with no type
kernel30.h:152: error: expected â€˜;â€™ before â€˜*â€™ token
make[2]: *** [threadELV3.o] Error 1
make[2]: Leaving directory `/peng/peng'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/peng'
make: *** [all-recursive-am] Error 2
Error by compilation !!!
peng# 



Any ideas?

---

### Post by llamakc on 2007-11-10
Is

```

sudo apt-get install penggy

```

not working?

---

### Post by Steveway on 2007-11-10
sudo apt-get install penggy
You don't need to compile it yourself.
EDIT: llamack was some seconds faster.

---

### Post by dtleigh on 2007-11-27
OK! So I dig myself further into this hole, but I really want to get Ubuntu connected through AOL.....

Have downloaded and decompressed penggy, entered this.....

root@derek-desktop:/penggy-0.2.1# ./configure
checking build system type... i686-pc-linux-gn
.
.
and got this......
.
checking for Guile... ./configure: line 10775: guile-config: command not found
configure: cannot find guile-config; is Guile installed?

Went into the the package manager and searched for Guile and found this.....

guile-1.6-libs
Main Guile libraries

....but still penggy configuration complains about not finding guile-config???

---

### Post by edm1 on 2007-11-27
Are you using broadband or dial-up. If broadband, i would highly recommend buying a router with a built in modem. If dial-up then...good luck.

---

### Post by angryfirelord on 2007-11-27
Which guile do you have installed? There's a guile 1.6 and guile 1.8 available. 

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=guile&searchon=names&subword=1&version=feisty&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=guile&searchon=names&subword=1&version=feisty&release=all")

---

### Post by dtleigh on 2007-11-29
I'm using Guile 1.6. 

If install 1.8 do I need to remove 1.6?

:(:(

---

### Post by angryfirelord on 2007-11-29
> **dtleigh said:**
> I'm using Guile 1.6. 

If install 1.8 do I need to remove 1.6?

:(:(
Yes, otherwise it could get confused. Don't know if that'll help you compile as that AOL program may require a much older guile if 1.8 doesn't work.

---

