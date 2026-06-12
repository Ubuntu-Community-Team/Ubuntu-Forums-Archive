---
title: "Compiling gcc for Linux From Scratc, stdio.h: No such file"
date: 2011-11-15
forum: Any Other OS
---

### Post by Mappenz on 2011-11-15
Hi,

I am trying to build Linux From Scratch and got stuck at chapter 5.5 GCC-4.6.1 Pass 1. My Hostsystem is Ubuntu 10.04. I had another error bevore, asm/errno.h was not found. But this problem seems to be gone. I'm not sure why, but if its really gone I am good with that.

Heres the output to the console, second try, without clean.

```

lfs@michi:/mnt/lfs/sources/gcc-build$ make
[ -f stage_final ] || echo stage3 > stage_final
make[1]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build'
make[2]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build'
make[3]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build'
rm -f stage_current
make[3]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build'
make[2]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build'
make[2]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build'
make[3]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/libiberty'
make[4]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/libiberty/testsuite'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/libiberty/testsuite'
make[3]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/libiberty'
make[3]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/lto-plugin'
make  all-am
make[4]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/lto-plugin'
make[4]: Für das Ziel »all-am« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/lto-plugin'
make[3]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/lto-plugin'
make[3]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp'
make  all-recursive
make[4]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp'
Making all in tests
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests'
Making all in .
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests'
make[6]: Für das Ziel »all-am« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests'
Making all in devel
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/devel'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/devel'
Making all in mpn
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpn'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpn'
Making all in mpz
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpz'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpz'
Making all in mpq
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpq'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpq'
Making all in mpf
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpf'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpf'
Making all in rand
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/rand'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/rand'
Making all in misc
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/misc'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/misc'
Making all in cxx
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/cxx'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/cxx'
Making all in mpbsd
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpbsd'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests/mpbsd'
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tests'
Making all in mpn
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpn'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpn'
Making all in mpz
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpz'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpz'
Making all in mpq
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpq'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpq'
Making all in mpf
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpf'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpf'
Making all in printf
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/printf'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/printf'
Making all in scanf
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/scanf'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/scanf'
Making all in cxx
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/cxx'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/cxx'
Making all in mpbsd
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpbsd'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/mpbsd'
Making all in demos
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos'
Making all in calc
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos/calc'
make  all-am
make[7]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos/calc'
make[7]: Für das Ziel »all-am« ist nichts zu tun.
make[7]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos/calc'
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos/calc'
Making all in expr
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos/expr'
make[6]: Für das Ziel »all« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos/expr'
make[6]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos'
make[6]: Für das Ziel »all-am« ist nichts zu tun.
make[6]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos'
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/demos'
Making all in tune
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tune'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/tune'
Making all in doc
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/doc'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp/doc'
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/gmp'
make[5]: Für das Ziel »all-am« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp'
make[4]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp'
make[3]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/gmp'
make[3]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/intl'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/intl'
make[3]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr'
Making all in doc
make[4]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/doc'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/doc'
Making all in src
make[4]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/src'
make  all-am
make[5]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALE_H=1 -DHAVE_WCHAR_H=1 -DHAVE_STDARG=1 -DHAVE_SYS_TIME_H=1 -DHAVE_ALLOCA_H=1 -DHAVE_STDINT_H=1 -DHAVE_VA_COPY=1 -DHAVE_SETLOCALE=1 -DHAVE_GETTIMEOFDAY=1 -DHAVE_LONG_LONG=1 -DHAVE_INTMAX_T=1 -DMPFR_HAVE_INTMAX_MAX=1 -DMPFR_HAVE_FESETROUND=1 -DHAVE_DENORMS=1 -DHAVE_ROUND=1 -DHAVE_TRUNC=1 -DHAVE_FLOOR=1 -DHAVE_CEIL=1 -DHAVE_NEARBYINT=1 -DHAVE_LDOUBLE_IEEE_EXT_LITTLE=1 -DMPFR_USE_THREAD_SAFE=1 -DLT_OBJDIR=\".libs/\" -DHAVE_ATTRIBUTE_MODE=1 -DHAVE___GMPN_ROOTREM=1 -DHAVE___GMPN_SBPI1_DIVAPPR_Q=1 -I. -I../../../gcc-4.6.1/mpfr/src   -I/mnt/lfs/sources/gcc-build/./gmp  -g -fkeep-inline-functions -MT exceptions.lo -MD -MP -MF .deps/exceptions.Tpo -c -o exceptions.lo ../../../gcc-4.6.1/mpfr/src/exceptions.c
libtool: compile:  gcc -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALE_H=1 -DHAVE_WCHAR_H=1 -DHAVE_STDARG=1 -DHAVE_SYS_TIME_H=1 -DHAVE_ALLOCA_H=1 -DHAVE_STDINT_H=1 -DHAVE_VA_COPY=1 -DHAVE_SETLOCALE=1 -DHAVE_GETTIMEOFDAY=1 -DHAVE_LONG_LONG=1 -DHAVE_INTMAX_T=1 -DMPFR_HAVE_INTMAX_MAX=1 -DMPFR_HAVE_FESETROUND=1 -DHAVE_DENORMS=1 -DHAVE_ROUND=1 -DHAVE_TRUNC=1 -DHAVE_FLOOR=1 -DHAVE_CEIL=1 -DHAVE_NEARBYINT=1 -DHAVE_LDOUBLE_IEEE_EXT_LITTLE=1 -DMPFR_USE_THREAD_SAFE=1 -DLT_OBJDIR=\".libs/\" -DHAVE_ATTRIBUTE_MODE=1 -DHAVE___GMPN_ROOTREM=1 -DHAVE___GMPN_SBPI1_DIVAPPR_Q=1 -I. -I../../../gcc-4.6.1/mpfr/src -I/mnt/lfs/sources/gcc-build/./gmp -g -fkeep-inline-functions -MT exceptions.lo -MD -MP -MF .deps/exceptions.Tpo -c ../../../gcc-4.6.1/mpfr/src/exceptions.c -o exceptions.o
In file included from ../../../gcc-4.6.1/mpfr/src/exceptions.c:23:0:
../../../gcc-4.6.1/mpfr/src/mpfr-impl.h:38:19: fatal error: stdio.h: No such file or directory
compilation terminated.
make[5]: *** [exceptions.lo] Fehler 1
make[5]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/src'
make[4]: *** [all] Fehler 2
make[4]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/src'
Making all in tests
make[4]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/tests'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/tests'
Making all in tune
make[4]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/tune'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr/tune'
make[4]: Betrete Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr'
make[4]: Für das Ziel »all-am« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr'
make[3]: *** [all-recursive] Fehler 1
make[3]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build/mpfr'
make[2]: *** [all-stage1-mpfr] Fehler 2
make[2]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build'
make[1]: *** [stage1-bubble] Fehler 2
make[1]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build'
make: *** [all] Fehler 2
```How do I fix this? The Problem is with the hostsystem, right?

This one is solved, but the next is waiting already

regards
Michael

---

### Post by Mappenz on 2011-11-15
After "working" on the Problem a little bit more it looks like I broke gcc:

```

lfs@michi:/mnt/lfs/sources/gcc-build$ ../gcc-4.6.1/configure \
>     --target=$LFS_TGT --prefix=/tools \
>     --disable-nls --disable-shared --disable-multilib \
>     --disable-decimal-float --disable-threads \
>     --disable-libmudflap --disable-libssp \
>     --disable-libgomp --disable-libquadmath \
>     --disable-target-libiberty --disable-target-zlib \
>     --enable-languages=c --without-ppl --without-cloog \
>     --with-mpfr-include=$(pwd)/../gcc-4.6.1/mpfr/src \
>     --with-mpfr-lib=$(pwd)/mpfr/src/.libs
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for a sed that does not truncate output... /bin/sed
checking for gawk... no
checking for mawk... mawk
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/mnt/lfs/sources/gcc-build':
configure: error: C compiler cannot create executables
See `config.log' for more details.



```

This subproblem is solved. Installing lib6-c did it.

---

### Post by Mappenz on 2011-11-15
.

---

### Post by Mappenz on 2011-11-15
I got a step further, but not in the last 1,5h. Shortened Output looks like this:

```

checking for i686-pc-linux-gnu-gcc...  /mnt/lfs/sources/gcc-build/./prev-gcc/xgcc -B/mnt/lfs/sources/gcc-build/./prev-gcc/ -B/tools/i686-pc-linux-gnu/bin/ -B/tools/i686-pc-linux-gnu/bin/ -B/tools/i686-pc-linux-gnu/lib/ -isystem /tools/i686-pc-linux-gnu/include -isystem /tools/i686-pc-linux-gnu/sys-include   
checking for C compiler default output file name... 
configure: error: in `/mnt/lfs/sources/gcc-build/lto-plugin':
configure: error: C compiler cannot create executables
See `config.log' for more details.
make[2]: *** [configure-stage2-lto-plugin] Fehler 77
make[2]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build'
make[1]: *** [stage2-bubble] Fehler 2
make[1]: Verlasse Verzeichnis '/mnt/lfs/sources/gcc-build'
make: *** [all] Fehler 2

```I could see where the Problem when I looked at config.log last time. This time I am clueless. Here is the logfile:
```

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.64.  Invocation command line was

  $ ../gcc-4.6.1/configure --target= --prefix=/tools --disable-nls --disable-shared --disable-multilib --disable-decimal-float --disable-threads --disable-libmudflap --disable-libssp --disable-libgomp --disable-libquadmath --disable-target-libiberty --disable-target-zlib --enable-languages=c --without-ppl --without-cloog --with-mpfr-include=/mnt/lfs/sources/gcc-build/../gcc-4.6.1/mpfr/src --with-mpfr-lib=/mnt/lfs/sources/gcc-build/mpfr/src/.libs

## --------- ##
## Platform. ##
## --------- ##

hostname = michi
uname -m = i686
uname -r = 2.6.38-12-generic
uname -s = Linux
uname -v = #51-Ubuntu SMP Wed Sep 28 14:25:20 UTC 2011

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/bin
PATH: /usr/bin
PATH: /bin
PATH: /usr/local/games
PATH: /usr/games
PATH: /usr/lib/jvm/java-6-sun-1.6.0.24/bin
PATH: /usr/lib/jvm/java-6-sun-1.6.0.24/lib
PATH: /usr/bin/java


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2222: checking build system type
configure:2236: result: i686-pc-linux-gnu
configure:2283: checking host system type
configure:2296: result: i686-pc-linux-gnu
configure:2316: checking target system type
configure:2329: result: i686-pc-linux-gnu
configure:2383: checking for a BSD-compatible install
configure:2451: result: /usr/bin/install -c
configure:2462: checking whether ln works
configure:2484: result: yes
configure:2488: checking whether ln -s works
configure:2492: result: yes
configure:2499: checking for a sed that does not truncate output
configure:2563: result: /bin/sed
configure:2572: checking for gawk
configure:2588: found /usr/bin/gawk
configure:2599: result: gawk
configure:3929: checking for gcc
configure:3945: found /usr/bin/gcc
configure:3956: result: gcc
configure:4185: checking for C compiler version
configure:4194: gcc --version >&5
gcc (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4205: $? = 0
configure:4194: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
configure:4205: $? = 0
configure:4194: gcc -V >&5
gcc: '-V' option must have argument
configure:4205: $? = 1
configure:4194: gcc -qversion >&5
gcc: unrecognized option '-qversion'
gcc: no input files
configure:4205: $? = 1
configure:4225: checking for C compiler default output file name
configure:4247: gcc    conftest.c  >&5
configure:4251: $? = 0
configure:4288: result: a.out
configure:4304: checking whether the C compiler works
configure:4313: ./a.out
configure:4317: $? = 0
configure:4332: result: yes
configure:4339: checking whether we are cross compiling
configure:4341: result: no
configure:4344: checking for suffix of executables
configure:4351: gcc -o conftest    conftest.c  >&5
configure:4355: $? = 0
configure:4377: result: 
configure:4383: checking for suffix of object files
configure:4405: gcc -c   conftest.c >&5
configure:4409: $? = 0
configure:4430: result: o
configure:4434: checking whether we are using the GNU C compiler
configure:4453: gcc -c   conftest.c >&5
configure:4453: $? = 0
configure:4462: result: yes
configure:4471: checking whether gcc accepts -g
configure:4491: gcc -c -g  conftest.c >&5
configure:4491: $? = 0
configure:4532: result: yes
configure:4549: checking for gcc option to accept ISO C89
configure:4613: gcc  -c -g -O2  conftest.c >&5
configure:4613: $? = 0
configure:4626: result: none needed
configure:4704: checking for g++
configure:4720: found /usr/bin/g++
configure:4731: result: g++
configure:4758: checking for C++ compiler version
configure:4767: g++ --version >&5
g++ (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4778: $? = 0
configure:4767: g++ -v >&5
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
configure:4778: $? = 0
configure:4767: g++ -V >&5
g++: '-V' option must have argument
configure:4778: $? = 1
configure:4767: g++ -qversion >&5
g++: unrecognized option '-qversion'
g++: no input files
configure:4778: $? = 1
configure:4782: checking whether we are using the GNU C++ compiler
configure:4801: g++ -c   conftest.cpp >&5
configure:4801: $? = 0
configure:4810: result: yes
configure:4819: checking whether g++ accepts -g
configure:4839: g++ -c -g  conftest.cpp >&5
configure:4839: $? = 0
configure:4880: result: yes
configure:4969: checking for gnatbind
configure:4999: result: no
configure:5061: checking for gnatmake
configure:5091: result: no
configure:5110: checking whether compiler driver understands Ada
configure:5133: result: no
configure:5142: checking how to compare bootstrapped objects
configure:5167: result: cmp --ignore-initial=16 $$f1 $$f2
configure:5183: checking for objdir
configure:5198: result: .libs
configure:7255: checking for default BUILD_CONFIG
configure:7287: result: bootstrap-debug
configure:7777: checking for bison
configure:7807: result: no
configure:7777: checking for byacc
configure:7807: result: no
configure:7777: checking for yacc
configure:7807: result: no
configure:7825: checking for bison
configure:7855: result: no
configure:7872: checking for gm4
configure:7902: result: no
configure:7872: checking for gnum4
configure:7902: result: no
configure:7872: checking for m4
configure:7902: result: no
configure:7919: checking for flex
configure:7949: result: no
configure:7919: checking for lex
configure:7949: result: no
configure:7967: checking for flex
configure:7997: result: no
configure:8014: checking for makeinfo
configure:8044: result: no
configure:8075: checking for expect
configure:8105: result: no
configure:8124: checking for runtest
configure:8154: result: no
configure:8269: checking for ar
configure:8285: found /usr/bin/ar
configure:8296: result: ar
configure:8410: checking for as
configure:8426: found /usr/bin/as
configure:8437: result: as
configure:8551: checking for dlltool
configure:8581: result: no
configure:8692: checking for ld
configure:8708: found /usr/bin/ld
configure:8719: result: ld
configure:8833: checking for lipo
configure:8863: result: no
configure:8974: checking for nm
configure:8990: found /usr/bin/nm
configure:9001: result: nm
configure:9115: checking for ranlib
configure:9131: found /usr/bin/ranlib
configure:9142: result: ranlib
configure:9251: checking for strip
configure:9267: found /usr/bin/strip
configure:9278: result: strip
configure:9387: checking for windres
configure:9417: result: no
configure:9528: checking for windmc
configure:9558: result: no
configure:9669: checking for objcopy
configure:9685: found /usr/bin/objcopy
configure:9696: result: objcopy
configure:9810: checking for objdump
configure:9826: found /usr/bin/objdump
configure:9837: result: objdump
configure:9990: checking for cc
configure:10006: found /usr/bin/cc
configure:10017: result: cc
configure:10151: checking for c++
configure:10167: found /usr/bin/c++
configure:10178: result: c++
configure:10312: checking for gcc
configure:10328: found /usr/bin/gcc
configure:10339: result: gcc
configure:10468: checking for gcj
configure:10498: result: no
configure:10629: checking for gfortran
configure:10659: result: no
configure:10790: checking for gccgo
configure:10820: result: no
configure:10881: checking for ar
configure:10899: found /tools/i686-pc-linux-gnu/bin/ar
configure:10911: result: /tools/i686-pc-linux-gnu/bin/ar
configure:11111: checking for as
configure:11129: found /tools/i686-pc-linux-gnu/bin/as
configure:11141: result: /tools/i686-pc-linux-gnu/bin/as
configure:11341: checking for dlltool
configure:11374: result: no
configure:11491: checking for dlltool
configure:11521: result: no
configure:11571: checking for ld
configure:11589: found /tools/i686-pc-linux-gnu/bin/ld
configure:11601: result: /tools/i686-pc-linux-gnu/bin/ld
configure:11801: checking for lipo
configure:11834: result: no
configure:11951: checking for lipo
configure:11981: result: no
configure:12031: checking for nm
configure:12049: found /tools/i686-pc-linux-gnu/bin/nm
configure:12061: result: /tools/i686-pc-linux-gnu/bin/nm
configure:12261: checking for objdump
configure:12279: found /tools/i686-pc-linux-gnu/bin/objdump
configure:12291: result: /tools/i686-pc-linux-gnu/bin/objdump
configure:12491: checking for ranlib
configure:12509: found /tools/i686-pc-linux-gnu/bin/ranlib
configure:12521: result: /tools/i686-pc-linux-gnu/bin/ranlib
configure:12721: checking for strip
configure:12739: found /tools/i686-pc-linux-gnu/bin/strip
configure:12751: result: /tools/i686-pc-linux-gnu/bin/strip
configure:12951: checking for windres
configure:12984: result: no
configure:13101: checking for windres
configure:13131: result: no
configure:13181: checking for windmc
configure:13214: result: no
configure:13331: checking for windmc
configure:13361: result: no
configure:13389: checking where to find the target ar
configure:13417: result: pre-installed in /tools/i686-pc-linux-gnu/bin
configure:13431: checking where to find the target as
configure:13459: result: pre-installed in /tools/i686-pc-linux-gnu/bin
configure:13473: checking where to find the target cc
configure:13496: result: just compiled
configure:13515: checking where to find the target c++
configure:13551: result: host tool
configure:13560: checking where to find the target c++ for libstdc++
configure:13596: result: host tool
configure:13605: checking where to find the target dlltool
configure:13638: result: host tool
configure:13647: checking where to find the target gcc
configure:13670: result: just compiled
configure:13689: checking where to find the target gcj
configure:13725: result: host tool
configure:13734: checking where to find the target gfortran
configure:13770: result: host tool
configure:13779: checking where to find the target gccgo
configure:13815: result: host tool
configure:13824: checking where to find the target ld
configure:13852: result: pre-installed in /tools/i686-pc-linux-gnu/bin
configure:13866: checking where to find the target lipo
configure:13888: result: host tool
configure:13897: checking where to find the target nm
configure:13925: result: pre-installed in /tools/i686-pc-linux-gnu/bin
configure:13939: checking where to find the target objdump
configure:13967: result: pre-installed in /tools/i686-pc-linux-gnu/bin
configure:13981: checking where to find the target ranlib
configure:14009: result: pre-installed in /tools/i686-pc-linux-gnu/bin
configure:14023: checking where to find the target strip
configure:14051: result: pre-installed in /tools/i686-pc-linux-gnu/bin
configure:14065: checking where to find the target windres
configure:14098: result: host tool
configure:14107: checking where to find the target windmc
configure:14140: result: host tool
configure:14177: checking whether to enable maintainer-specific portions of Makefiles
configure:14186: result: no
configure:14219: checking whether -fkeep-inline-functions is supported
configure:14238: gcc -c -g -O2 -fkeep-inline-functions  conftest.c >&5
configure:14238: $? = 0
configure:14239: result: yes
configure:14436: creating ./config.status

## ---------------------- ##
## Running config.status. ##
## ---------------------- ##

This file was extended by config.status, which was
generated by GNU Autoconf 2.64.  Invocation command line was

  CONFIG_FILES    = 
  CONFIG_HEADERS  = 
  CONFIG_LINKS    = 
  CONFIG_COMMANDS = 
  $ ./config.status 

on michi

config.status:958: creating Makefile

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_AR_FOR_TARGET_set=
ac_cv_env_AR_FOR_TARGET_value=
ac_cv_env_AR_set=
ac_cv_env_AR_value=
ac_cv_env_AS_FOR_TARGET_set=
ac_cv_env_AS_FOR_TARGET_value=
ac_cv_env_AS_set=
ac_cv_env_AS_value=
ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CC_FOR_TARGET_set=
ac_cv_env_CC_FOR_TARGET_value=
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_FOR_TARGET_set=
ac_cv_env_CXX_FOR_TARGET_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_DLLTOOL_FOR_TARGET_set=
ac_cv_env_DLLTOOL_FOR_TARGET_value=
ac_cv_env_DLLTOOL_set=
ac_cv_env_DLLTOOL_value=
ac_cv_env_GCC_FOR_TARGET_set=
ac_cv_env_GCC_FOR_TARGET_value=
ac_cv_env_GCJ_FOR_TARGET_set=
ac_cv_env_GCJ_FOR_TARGET_value=
ac_cv_env_GFORTRAN_FOR_TARGET_set=
ac_cv_env_GFORTRAN_FOR_TARGET_value=
ac_cv_env_GOC_FOR_TARGET_set=
ac_cv_env_GOC_FOR_TARGET_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LD_FOR_TARGET_set=
ac_cv_env_LD_FOR_TARGET_value=
ac_cv_env_LD_set=
ac_cv_env_LD_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_LIPO_FOR_TARGET_set=
ac_cv_env_LIPO_FOR_TARGET_value=
ac_cv_env_LIPO_set=
ac_cv_env_LIPO_value=
ac_cv_env_NM_FOR_TARGET_set=
ac_cv_env_NM_FOR_TARGET_value=
ac_cv_env_NM_set=
ac_cv_env_NM_value=
ac_cv_env_OBJCOPY_set=
ac_cv_env_OBJCOPY_value=
ac_cv_env_OBJDUMP_FOR_TARGET_set=
ac_cv_env_OBJDUMP_FOR_TARGET_value=
ac_cv_env_OBJDUMP_set=
ac_cv_env_OBJDUMP_value=
ac_cv_env_RANLIB_FOR_TARGET_set=
ac_cv_env_RANLIB_FOR_TARGET_value=
ac_cv_env_RANLIB_set=
ac_cv_env_RANLIB_value=
ac_cv_env_STRIP_FOR_TARGET_set=
ac_cv_env_STRIP_FOR_TARGET_value=
ac_cv_env_STRIP_set=
ac_cv_env_STRIP_value=
ac_cv_env_WINDMC_FOR_TARGET_set=
ac_cv_env_WINDMC_FOR_TARGET_value=
ac_cv_env_WINDMC_set=
ac_cv_env_WINDMC_value=
ac_cv_env_WINDRES_FOR_TARGET_set=
ac_cv_env_WINDRES_FOR_TARGET_value=
ac_cv_env_WINDRES_set=
ac_cv_env_WINDRES_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_build_configargs_set=
ac_cv_env_build_configargs_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_host_configargs_set=
ac_cv_env_host_configargs_value=
ac_cv_env_target_alias_set=set
ac_cv_env_target_alias_value=
ac_cv_env_target_configargs_set=
ac_cv_env_target_configargs_value=
ac_cv_host=i686-pc-linux-gnu
ac_cv_objext=o
ac_cv_path_AR_FOR_TARGET=/tools/i686-pc-linux-gnu/bin/ar
ac_cv_path_AS_FOR_TARGET=/tools/i686-pc-linux-gnu/bin/as
ac_cv_path_LD_FOR_TARGET=/tools/i686-pc-linux-gnu/bin/ld
ac_cv_path_NM_FOR_TARGET=/tools/i686-pc-linux-gnu/bin/nm
ac_cv_path_OBJDUMP_FOR_TARGET=/tools/i686-pc-linux-gnu/bin/objdump
ac_cv_path_RANLIB_FOR_TARGET=/tools/i686-pc-linux-gnu/bin/ranlib
ac_cv_path_SED=/bin/sed
ac_cv_path_STRIP_FOR_TARGET=/tools/i686-pc-linux-gnu/bin/strip
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AR=ar
ac_cv_prog_AS=as
ac_cv_prog_AWK=gawk
ac_cv_prog_CC_FOR_TARGET=cc
ac_cv_prog_CXX_FOR_TARGET=c++
ac_cv_prog_GCC_FOR_TARGET=gcc
ac_cv_prog_LD=ld
ac_cv_prog_NM=nm
ac_cv_prog_OBJCOPY=objcopy
ac_cv_prog_OBJDUMP=objdump
ac_cv_prog_RANLIB=ranlib
ac_cv_prog_STRIP=strip
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_cxx_g=yes
ac_cv_target=i686-pc-linux-gnu
acx_cv_cc_gcc_supports_ada=no
acx_cv_prog_LN=ln
gcc_cv_prog_cmp_skip='cmp --ignore-initial=16 $$f1 $$f2'
gcc_cv_tool_dirs=/tools/libexec/gcc/i686-pc-linux-gnu/4.6.1:/tools/libexec/gcc/i686-pc-linux-gnu:/usr/lib/gcc/i686-pc-linux-gnu/4.6.1:/usr/lib/gcc/i686-pc-linux-gnu:/tools/i686-pc-linux-gnu/bin/i686-pc-linux-gnu/4.6.1:/tools/i686-pc-linux-gnu/bin:
gcc_cv_tool_prefix=/tools
lt_cv_objdir=.libs

## ----------------- ##
## Output variables. ##
## ----------------- ##

AR='ar'
AR_FOR_BUILD='$(AR)'
AR_FOR_TARGET='/tools/i686-pc-linux-gnu/bin/ar'
AS='as'
AS_FOR_BUILD='$(AS)'
AS_FOR_TARGET='/tools/i686-pc-linux-gnu/bin/as'
AWK='gawk'
BISON='/mnt/lfs/sources/gcc-4.6.1/missing bison'
BUILD_CONFIG='bootstrap-debug'
CC='gcc'
CC_FOR_BUILD='$(CC)'
CC_FOR_TARGET='$$r/$(HOST_SUBDIR)/gcc/xgcc -B$$r/$(HOST_SUBDIR)/gcc/'
CFLAGS='-g -O2'
CFLAGS_FOR_BUILD='-g -O2'
CFLAGS_FOR_TARGET='-g -O2'
COMPILER_AS_FOR_TARGET='$$r/$(HOST_SUBDIR)/gcc/as'
COMPILER_LD_FOR_TARGET='$$r/$(HOST_SUBDIR)/gcc/collect-ld'
COMPILER_NM_FOR_TARGET='$$r/$(HOST_SUBDIR)/gcc/nm'
CONFIGURE_GDB_TK=''
CPPFLAGS=''
CXX='g++'
CXXFLAGS='-g -O2'
CXXFLAGS_FOR_BUILD='-g -O2'
CXXFLAGS_FOR_TARGET='-g -O2'
CXX_FOR_BUILD='$(CXX)'
CXX_FOR_TARGET='$(CXX)'
DEBUG_PREFIX_CFLAGS_FOR_TARGET=''
DEFS='-DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE_URL=\"\" -DLT_OBJDIR=\".libs/\"'
DLLTOOL='dlltool'
DLLTOOL_FOR_BUILD='$(DLLTOOL)'
DLLTOOL_FOR_TARGET='$(DLLTOOL)'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EXEEXT=''
EXPECT='expect'
FLAGS_FOR_TARGET=' -B$(build_tooldir)/bin/ -B$(build_tooldir)/lib/ -isystem $(build_tooldir)/include -isystem $(build_tooldir)/sys-include'
FLEX='/mnt/lfs/sources/gcc-4.6.1/missing flex'
GCC_FOR_TARGET='$$r/$(HOST_SUBDIR)/gcc/xgcc -B$$r/$(HOST_SUBDIR)/gcc/'
GCC_SHLIB_SUBDIR=''
GCJ_FOR_BUILD='$(GCJ)'
GCJ_FOR_TARGET='$(GCJ)'
GDB_TK=''
GFORTRAN_FOR_BUILD='$(GFORTRAN)'
GFORTRAN_FOR_TARGET='$(GFORTRAN)'
GNATBIND='no'
GNATMAKE='no'
GOC_FOR_BUILD='$(GOC)'
GOC_FOR_TARGET='$(GOC)'
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_GDB_TK=''
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
LD='ld'
LDFLAGS=''
LDFLAGS_FOR_BUILD=''
LD_FOR_BUILD='$(LD)'
LD_FOR_TARGET='/tools/i686-pc-linux-gnu/bin/ld'
LEX='/mnt/lfs/sources/gcc-4.6.1/missing flex'
LIBOBJS=''
LIBS=''
LIPO='lipo'
LIPO_FOR_TARGET='$(LIPO)'
LN='ln'
LN_S='ln -s'
LTLIBOBJS=''
M4='/mnt/lfs/sources/gcc-4.6.1/missing m4'
MAINT='#'
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAKEINFO='/mnt/lfs/sources/gcc-4.6.1/missing makeinfo'
NM='nm'
NM_FOR_BUILD='$(NM)'
NM_FOR_TARGET='/tools/i686-pc-linux-gnu/bin/nm'
OBJCOPY='objcopy'
OBJDUMP='objdump'
OBJDUMP_FOR_TARGET='/tools/i686-pc-linux-gnu/bin/objdump'
OBJEXT='o'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_URL=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
RANLIB='ranlib'
RANLIB_FOR_BUILD='$(RANLIB)'
RANLIB_FOR_TARGET='/tools/i686-pc-linux-gnu/bin/ranlib'
RAW_CXX_FOR_TARGET='$(CXX)'
RPATH_ENVVAR='LD_LIBRARY_PATH'
RUNTEST='runtest'
SED='/bin/sed'
SHELL='/bin/sh'
STRIP='strip'
STRIP_FOR_TARGET='/tools/i686-pc-linux-gnu/bin/strip'
SYSROOT_CFLAGS_FOR_TARGET=''
TOPLEVEL_CONFIGURE_ARGUMENTS='../gcc-4.6.1/configure --target= --prefix=/tools --disable-nls --disable-shared --disable-multilib --disable-decimal-float --disable-threads --disable-libmudflap --disable-libssp --disable-libgomp --disable-libquadmath --disable-target-libiberty --disable-target-zlib --enable-languages=c --without-ppl --without-cloog --with-mpfr-include=/mnt/lfs/sources/gcc-build/../gcc-4.6.1/mpfr/src --with-mpfr-lib=/mnt/lfs/sources/gcc-build/mpfr/src/.libs'
WINDMC='windmc'
WINDMC_FOR_BUILD='$(WINDMC)'
WINDMC_FOR_TARGET='$(WINDMC)'
WINDRES='windres'
WINDRES_FOR_BUILD='$(WINDRES)'
WINDRES_FOR_TARGET='$(WINDRES)'
YACC='/mnt/lfs/sources/gcc-4.6.1/missing bison -y'
ac_ct_CC='gcc'
ac_ct_CXX='g++'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_configargs=' --cache-file=../config.cache '\''--prefix=/tools'\'' '\''--disable-nls'\'' '\''--disable-shared'\'' '\''--disable-multilib'\'' '\''--disable-decimal-float'\'' '\''--disable-threads'\'' '\''--disable-libmudflap'\'' '\''--disable-libssp'\'' '\''--disable-libgomp'\'' '\''--disable-libquadmath'\'' '\''--disable-target-libiberty'\'' '\''--disable-target-zlib'\'' '\''--without-ppl'\'' '\''--without-cloog'\'' '\''--with-mpfr-include=/mnt/lfs/sources/gcc-build/../gcc-4.6.1/mpfr/src'\'' '\''--with-mpfr-lib=/mnt/lfs/sources/gcc-build/mpfr/src/.libs'\'' '\''--enable-languages=c,lto'\'' --program-transform-name='\''s,y,y,'\'' --disable-option-checking'
build_configdirs=' libiberty fixincludes'
build_cpu='i686'
build_libsubdir='build-i686-pc-linux-gnu'
build_noncanonical='i686-pc-linux-gnu'
build_os='linux-gnu'
build_subdir='build-i686-pc-linux-gnu'
build_tooldir='${exec_prefix}/i686-pc-linux-gnu'
build_vendor='pc'
clooginc=''
clooglibs=''
compare_exclusions='gcc/cc*-checksum$(objext) | gcc/ada/*tools/*'
config_shell='/bin/sh'
configdirs=' intl libiberty zlib libcpp libdecnumber gmp mpfr mpc fixincludes gcc lto-plugin'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
do_compare='cmp --ignore-initial=16 $$f1 $$f2'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='${prefix}'
extra_host_libiberty_configure_flags='--enable-shared'
extra_mpc_gmp_configure_flags='--with-gmp-include=$$r/$(HOST_SUBDIR)/gmp --with-gmp-lib=$$r/$(HOST_SUBDIR)/gmp/.libs'
extra_mpc_mpfr_configure_flags=''
extra_mpfr_configure_flags='--with-gmp-include=$$r/$(HOST_SUBDIR)/gmp --with-gmp-lib=$$r/$(HOST_SUBDIR)/gmp/.libs'
gmpinc='-I$$r/$(HOST_SUBDIR)/gmp -I$$s/gmp -I/mnt/lfs/sources/gcc-build/../gcc-4.6.1/mpfr/src -I$$s/mpc/src '
gmplibs='-L$$r/$(HOST_SUBDIR)/gmp/.libs -L/mnt/lfs/sources/gcc-build/mpfr/src/.libs -L$$r/$(HOST_SUBDIR)/mpc/src/.libs -lmpc -lmpfr -lgmp'
host='i686-pc-linux-gnu'
host_alias=''
host_configargs=' --cache-file=./config.cache  '\''--prefix=/tools'\'' '\''--disable-nls'\'' '\''--disable-shared'\'' '\''--disable-multilib'\'' '\''--disable-decimal-float'\'' '\''--disable-threads'\'' '\''--disable-libmudflap'\'' '\''--disable-libssp'\'' '\''--disable-libgomp'\'' '\''--disable-libquadmath'\'' '\''--disable-target-libiberty'\'' '\''--disable-target-zlib'\'' '\''--without-ppl'\'' '\''--without-cloog'\'' '\''--with-mpfr-include=/mnt/lfs/sources/gcc-build/../gcc-4.6.1/mpfr/src'\'' '\''--with-mpfr-lib=/mnt/lfs/sources/gcc-build/mpfr/src/.libs'\'' '\''--enable-languages=c,lto'\'' --program-transform-name='\''s,y,y,'\'' --disable-option-checking'
host_cpu='i686'
host_noncanonical='i686-pc-linux-gnu'
host_os='linux-gnu'
host_subdir='.'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
oldincludedir='/usr/include'
pdfdir='${docdir}'
poststage1_ldflags='-static-libstdc++ -static-libgcc'
poststage1_libs=''
pplinc=''
ppllibs=''
prefix='/tools'
program_transform_name='s,y,y,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
stage1_cflags='-g -fkeep-inline-functions'
stage1_checking='--enable-checking=yes,types'
stage1_languages='c,lto'
stage1_ldflags=''
stage1_libs=''
stage2_werror_flag=''
sysconfdir='${prefix}/etc'
target='i686-pc-linux-gnu'
target_alias=''
target_configargs='--cache-file=./config.cache   '\''--prefix=/tools'\'' '\''--disable-nls'\'' '\''--disable-shared'\'' '\''--disable-multilib'\'' '\''--disable-decimal-float'\'' '\''--disable-threads'\'' '\''--disable-libmudflap'\'' '\''--disable-libssp'\'' '\''--disable-libgomp'\'' '\''--disable-libquadmath'\'' '\''--disable-target-libiberty'\'' '\''--disable-target-zlib'\'' '\''--without-ppl'\'' '\''--without-cloog'\'' '\''--with-mpfr-include=/mnt/lfs/sources/gcc-build/../gcc-4.6.1/mpfr/src'\'' '\''--with-mpfr-lib=/mnt/lfs/sources/gcc-build/mpfr/src/.libs'\'' '\''--enable-languages=c,lto'\'' --program-transform-name='\''s,y,y,'\'' --disable-option-checking'
target_configdirs=' libgcc'
target_cpu='i686'
target_noncanonical='i686-pc-linux-gnu'
target_os='linux-gnu'
target_subdir='i686-pc-linux-gnu'
target_vendor='pc'
tooldir='${exec_prefix}/i686-pc-linux-gnu'

## ------------------- ##
## File substitutions. ##
## ------------------- ##

alphaieee_frag='/dev/null'
host_makefile_frag='../gcc-4.6.1/config/mh-x86omitfp'
ospace_frag='/dev/null'
serialization_dependencies='serdep.tmp'
target_makefile_frag='../gcc-4.6.1/config/mt-gnu'

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""
#define PACKAGE_URL ""
#define LT_OBJDIR ".libs/"

configure: exit 0
```

Most people solve "configure: error: C compiler cannot create executables" by installing build-essentials. I have that package installed. Any ideas?

---

