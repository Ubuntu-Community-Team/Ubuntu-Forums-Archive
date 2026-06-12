---
title: "Help on MAKE ; )"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2006-10-10
](*,)    Hi Guys,  can anyone tell me why I get this when I use make on ndiswrapper in Edgy  ??

Thanks

bill@bill-desktop2:~/ndiswrapper-1.25$ make
make -C driver
make[1]: Entering directory `/home/bill/ndiswrapper-1.25/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/bill/ndiswrapper-1.25/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/home/bill/ndiswrapper-1.25/driver'
make -C utils
make[1]: Entering directory `/home/bill/ndiswrapper-1.25/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)

---

### Post by hw-tph on 2006-10-11
1. Why not use the included ndiswrapper module and utils from the repositories (it's in Universe).

2. You need to install the development packages, including the headers for your running kernel (**sudo apt-get install linux-headers-$(uname -r)**)


Håkan

---

### Post by MrKlean on 2006-10-11
Thanks, but how do I get to the repos without a connection >>  and what are the developement packages ??  I'm new to this and had it working once, now I can't get it to do squat LOL!!
Thanks again ; )

---

### Post by MrKlean on 2006-10-11
Another question?? if you can please..  stdlib.h is a missing file or directory.. What puts that files where it should go ??  Is it a driver file or a Ubuntu file ??
Thanks ; )

---

### Post by Frak on 2006-10-11
It's in saynaptics, isn't it?

---

### Post by Frak on 2006-10-11
For the ones on on repos, go to your local library and go to packages.ubuntu.com and download to floppy(thats what I did for ndiswrapper gtk) but the ndiswrapper is on the Ubuntu installation CD go to synapt -> edit -> add CD, go to ndiswrapper, there you go!(one with CD is text based), I had to do it that way because my apartment is a hotspot. I don't own the internet, just use it.

---

