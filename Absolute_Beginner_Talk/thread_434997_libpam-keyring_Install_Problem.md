---
title: "libpam-keyring Install Problem"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by holmb101 on 2007-05-06
While trying to install libpam-keyring I keep getting this error.  I have tried this with sudo privileges, but I get the same error.  

jim@jim-laptop:/tmp/pam_keyring-0.0.8$ ./configure --prefix=/usr --libdir=/lib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
**configure: error: cannot run /bin/bash ./config.sub**

Another question: Every tutorial I have read about getting rid of the keyring password says that I can install libpam-keyring with apt-get.  However apt-get cannot find this package.  I have opened all of the repositories and updated apt-get, yet I still cannot find it.

---

### Post by tgm4883 on 2007-05-06
Are you using feisty?  I don't think it was available back in edgy

---

### Post by holmb101 on 2007-05-06
No, I'm using Edgy. 
That would explain why I can't find it.

Is there a similar fix for Edgy?

---

### Post by AtrejuT on 2007-05-06
yeah, there's also libpam-keyring available in edgy, just not in the repositories.
there is a debian package here, though:
[http://ubuntuforums.org/showthread.php?t=192281&highlight=libpam-keyring](http://ubuntuforums.org/showthread.php?t=192281&highlight=libpam-keyring)
(couple posts down, from yopnono)

hope that will help

---

