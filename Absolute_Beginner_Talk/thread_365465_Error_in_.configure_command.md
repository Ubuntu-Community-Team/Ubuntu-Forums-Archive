---
title: "Error in ./configure command"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by gingerj on 2007-02-19
Hi all,

I'm running the Ubuntu Dapper Drake build (6.06), and I'm having **extreme** problems trying to use the ./configure and make commands to rebuild my sound card drivers.

First of all the package to allow me to input these commands wasn't included by default, after finding that out. I installed them, now I'm getting this error when I run the ./configure command and it won't even let me do a make command.

> 
:~/Desktop/alsa-driver-1.0.14rc2$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/james/Desktop/alsa-driver-1.0.14rc2
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


Any idea's why it's complaining about my kernal? Err well confused... Did the package that I did a sudo apt-get for not install correctly or is my repository incorrect for the package build? Erm could anyone shed some light on this problem.

---

### Post by Sqwishy on 2007-02-19
you need your kernel's source code stuffs. So in synaptic look for the kernel you're using and download the source.

---

### Post by doobit on 2007-02-19
./configure is saying you don't have a file you need to compile alsa. I'm curious as to why you don't just reinstall the one from the Ubuntu repositories using Synaptic? That would be a lot easier.

---

