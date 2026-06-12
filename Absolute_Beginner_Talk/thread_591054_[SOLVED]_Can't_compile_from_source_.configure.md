---
title: "[SOLVED] Can't compile from source ./configure"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-25
I'm missing C compiler. What do I have to install in order to compile programs from the sourcecode?

After ./configure I'm getting this error:

> ~/Desktop/pidgin-2.2.2$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


---

### Post by Maestro23 on 2007-10-25
Do you have build-essential.

> sudo apt-get install build-essential

---

### Post by Kosimo on 2007-10-25
> **Maestro23 said:**
> Do you have build-essential.

Yeps... Thanks, I always forget to install build-essential ;)

---

### Post by Maestro23 on 2007-10-25
> **Kosimo said:**
> Yeps... Thanks, I always forget to install build-essential ;)

No prob.  Please mark this SOLVED using Thread Tools.

Thanks. :)

---

### Post by Kosimo on 2007-10-25
Done

---

