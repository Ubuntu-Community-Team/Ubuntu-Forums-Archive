---
title: "C compiler cannot create executables"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by DToolan on 2005-11-05
I am trying to install an AVR (microcontroller) target of gcc on a Linux system (Ubuntu) so I downloaded the following into a /tmp/avr directory...

binutils-2.16.1
gcc-3.4.4
avr-libc-1.2.3
uisp-20050207

First, I extracted the binutils and then created the directory /tmp/avr/binutils-2.16.1/obj-avr

From this directory I issued the following (and got the following error)...

> root@ubuntu:/tmp/avr/binutils-2.16.1/obj-avr# ../configure --target=avr --prefix=/usr/local/avr --disable-nls
loading cache ./config.cache
checking host system type... i686-pc-linux-gnulibc1
checking target system type... avr-unknown-none
checking build system type... i686-pc-linux-gnulibc1
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking whether the C compiler (gcc ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

I understand what it is telling me (that it tried to compile a short test program and got no result). What I don't know is why or where to go from here. As far as I can tell, there is a gcc version presently installed and should work...

> root@ubuntu:/tmp/avr/binutils-2.16.1/obj-avr# gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,tre elang --prefix=/usr --with-gxx-include-dir=/usr/include/c++/4.0.2 --enable-shared - -with-system-zlib --libexecdir=/usr/lib --enable-nls --without-included-gettext --e nable-threads=posix --program-suffix=-4.0 --enable-__cxa_atexit --enable-libstdcxx- allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-gc=boehm - -enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gc j-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release i486-lin ux-gnu
Thread model: posix
gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Any ideas on what I should check? Oh... and I'm a Linux newbie so be nice :)

---

### Post by DToolan on 2005-11-05
Nevermind... found a post here with the solution (needed to install "build-essentials" with synaptic).  All works now... Thanx

---

