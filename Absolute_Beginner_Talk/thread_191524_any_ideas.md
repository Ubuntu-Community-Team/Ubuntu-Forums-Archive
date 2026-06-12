---
title: "any ideas?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by voiceofxile on 2006-06-07
I have build-essential installed, and when I ./configure   I get a message saying my compiler can't create executables.  The goal is to have wine-0.9.14, but I can't get past this step. Can someone help me make sence of the config.log?


configure:1832: $? = 0
configure:1834: gcc -m32 -v </dev/null >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --l$Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
configure:1837: $? = 0
configure:1839: gcc -m32 -V </dev/null >&5
gcc: '-V' must come at the start of the command line
configure:1842: $? = 1
configure:1865: checking for C compiler default output file name
configure:1868: gcc -m32    conftest.c  >&5
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.0.3/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
configure:1871: $? = 1
configure: failed program was:
| /* confdefs.h.  */

Any ideas would be most appreciated, as I am new to this.   ](*,)

---

### Post by Estariel on 2006-06-07
if you follow this [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) I suppose you do not have to compile it yourself. I haven't read through it carefully though, and I do not use wine.
But this seems to be wineHQs official repository, and they should have the latest version.

---

