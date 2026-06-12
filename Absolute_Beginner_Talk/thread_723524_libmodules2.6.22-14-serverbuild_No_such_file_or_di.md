---
title: "lib/modules/2.6.22-14-server/build: No such file or directory."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by medha on 2008-03-13
I installed ubuntu server and everytime I  make, it gives the error:
make -C /lib/modules/2.6.22-14-server/build M=/home/user/ modules
make: *** /lib/modules/2.6.22-14-server/build: No such file or directory.  Stop.
make: *** [prog-modules] Error 2

Installing linux headers does not work.

Any ideas?
Thanks!

---

### Post by dca on 2008-03-13
Have you installed the 'build-essential' package?

---

### Post by speedrender on 2008-03-15
Hey dca,

It's funny, I'm going through the same thing now.  I'm a total noob and trying to run make on a system I just installed a few days ago.  Also got the same message.

[I][B]jeff@ubuntu:~/2007_1210_RT61_Linux_STA_v1.1.2.0/Module$ make all
make -C /lib/modules/2.6.22-14-server/build SUBDIRS=/home/jeff/2007_1210_RT61_Linux_STA_v1.1.2.0/Module modules
make: *** /lib/modules/2.6.22-14-server/build: No such file or directory.  Stop.
make: *** [all] Error 2
jeff@ubuntu:~/2007_1210_RT61_Linux_STA_v1.1.2.0/Module$[/I][/B]

After a Google search, I found this thread and installed the "build-essential" package with:

***sudo apt-get installed build-essential***

Several libraries were install, but after all this, I still get the same error as above.

I checked the directory /lib/modules/2.6.22-14-server but didn't see a build directory.  I'm sure I'm missing something, I just don't know what it is yet.  :)

[I][B]jeff@ubuntu:/lib/modules/2.6.22-14-server$ ls -l
total 1712
drwxr-xr-x  2 root root   4096 2008-03-13 08:30 initrd
drwxr-xr-x 10 root root   4096 2008-03-13 08:30 kernel
-rw-r--r--  1 root root 363151 2008-03-13 08:30 modules.alias
-rw-r--r--  1 root root     69 2008-03-13 08:30 modules.ccwmap
-rw-r--r--  1 root root 388994 2008-03-13 08:30 modules.dep
-rw-r--r--  1 root root    813 2008-03-13 08:30 modules.ieee1394map
-rw-r--r--  1 root root    527 2008-03-13 08:30 modules.inputmap
-rw-r--r--  1 root root  17714 2008-03-13 08:30 modules.isapnpmap
-rw-r--r--  1 root root     74 2008-03-13 08:30 modules.ofmap
-rw-r--r--  1 root root 270369 2008-03-13 08:30 modules.pcimap
-rw-r--r--  1 root root   1345 2008-03-13 08:30 modules.seriomap
-rw-r--r--  1 root root 165593 2008-03-13 08:30 modules.symbols
-rw-r--r--  1 root root 479477 2008-03-13 08:30 modules.usbmap
drwxr-xr-x 10 root root   4096 2008-03-13 08:30 ubuntu
jeff@ubuntu:/lib/modules/2.6.22-14-server$[/I][/B]

Any help is very much appreciated.

---

