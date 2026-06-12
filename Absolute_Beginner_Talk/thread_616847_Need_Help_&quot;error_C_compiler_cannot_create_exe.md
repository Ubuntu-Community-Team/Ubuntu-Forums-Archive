---
title: "Need Help: &quot;error: C compiler cannot create executables&quot;"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by ES_EF_EX on 2007-11-18
I'm trying to configure Snoop, and I keep getting this message when I run ./configure

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

I have no clue what to do.  I searched via Google and I couldnt get much help from there.  Here is the entire Terminal output: 

comp@xxxxxx:~/Desktop/snoop-0.3.0$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking OS...  Linux 
checking kernel...  2.6.20-16-generic 
checking kernel build tree...  found in /lib/modules/2.6.20-16-generic/build (building for 2.6.20-16-generic)
checking kernel support...  supported in kernel/Linux/2.6 
checking kernel for class_simple... not used.
checking kernel for RCU fdtable... used.
checking kernel for *parent in class_device_create... used.
checking kernel for RCU PID hash... used.
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Any help is much appreciated :)

---

### Post by Paul820 on 2007-11-18
Do you have build-essential? From the terminal
> sudo aptitude install build-essential

---

