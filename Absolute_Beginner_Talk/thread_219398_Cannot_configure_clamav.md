---
title: "Cannot configure clamav"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Ganggang on 2006-07-19
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
creating target.h - canonical system defines
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
[B]checking for C compiler default output file name... configure: error: C compiler cannot create executables
[/B]
See `config.log' for more details.


can someone tell me why i got this error???

Thx

---

### Post by orb9220 on 2006-07-20
why are you trying to compile it when it is already in synaptic ready to install?

---

### Post by slimdog360 on 2006-07-20
```
sudo apt-get install build-essential
```
then try again

---

