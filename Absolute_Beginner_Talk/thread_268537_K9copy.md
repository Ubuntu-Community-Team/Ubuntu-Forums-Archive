---
title: "K9copy"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Zone17 on 2006-09-30
I am very new to ubuntu and I am trying to install K9copy but keep getting no acceptable C compiler found in $PATH message. Any suggestions?

zone@zone-laptop:~/k9copy-1.1.0-beta1$
zone@zone-laptop:~/k9copy-1.1.0-beta1$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by llamakc on 2006-09-30
That's in the repositories:

apt-cache show k9copy
Package: k9copy
Priority: optional
Section: universe/kde
Installed-Size: 1688
Maintainer: Anthony Mercatante <tonio@ubuntu.com>
Architecture: i386
Version: 1.1.0~beta1-0ubuntu1


sudo apt-get install k9copy

Or, if you must build it, install the package "build-essential"

---

### Post by Zone17 on 2006-09-30
Thanks!

---

