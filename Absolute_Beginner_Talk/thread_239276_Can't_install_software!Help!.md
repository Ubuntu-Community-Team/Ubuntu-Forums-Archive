---
title: "Can't install software!Help!"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by thorium on 2006-08-19
thorium@localhost:~/kbsbbs-2.0dev$ ./configure --prefix=/home/bbs
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for style of include used by make... none
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
](*,) 
Am I wrong?
I installed softwares in this way on GentooLinux successfully.

---

### Post by secretlondon on 2006-08-19
> **thorium said:**
> 
I installed softwares in this way on GentooLinux successfully.

Ok - the easiest way is to install binary packages - .deb files, rather than try and compile your own. To do that you use synaptic which is in the system/administration menu in gnome.

Does this help - or are you trying to install software that isn't in the repositories?

---

### Post by Polygon on 2006-08-19
other people have suggested that installing "build-essential" and its dependencies will solve the problem, try that.

---

### Post by aysiu on 2006-08-19
What's the name of the package you're trying to install?

---

### Post by thorium on 2006-08-30
> **Polygon said:**
> other people have suggested that installing "build-essential" and its dependencies will solve the problem, try that.


It's the right answer for me!!
Thanks!

---

