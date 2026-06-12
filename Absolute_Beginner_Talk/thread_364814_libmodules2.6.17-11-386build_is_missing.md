---
title: "/lib/modules/2.6.17-11-386/build is missing"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by DesiSinger on 2007-02-18
Hello,

Below is error I'm getting while trying to run 'make'.

I was trying to install the madwifi for my wlan.
Error:

student@Ubuntu610:~/Desktop/madwifi-0.9.2.1$ sudo make
cd: 1: can't cd to /lib/modules/2.6.17-11-386/build
Makefile.inc:89: *** /lib/modules/2.6.17-11-386/build is missing, please set KERNELPATH.  Stop.


Below is what I have under /lib/modules/2.6.17-11-386

student@Ubuntu610:/lib/modules/2.6.17-11-386$ ls -l
total 1520
drwxr-xr-x  2 root root   4096 2007-02-16 00:01 initrd
drwxr-xr-x 11 root root   4096 2007-02-16 00:01 kernel
drwxr-xr-x  2 root root   4096 2007-02-16 00:01 madwifi
-rw-r--r--  1 root root 330352 2007-02-16 00:03 modules.alias
-rw-r--r--  1 root root     69 2007-02-16 00:03 modules.ccwmap
-rw-r--r--  1 root root 340199 2007-02-16 00:03 modules.dep
-rw-r--r--  1 root root    813 2007-02-16 00:03 modules.ieee1394map
-rw-r--r--  1 root root    806 2007-02-16 00:03 modules.inputmap
-rw-r--r--  1 root root  22378 2007-02-16 00:03 modules.isapnpmap
-rw-r--r--  1 root root     74 2007-02-16 00:03 modules.ofmap
-rw-r--r--  1 root root 265637 2007-02-16 00:03 modules.pcimap
-rw-r--r--  1 root root   1135 2007-02-16 00:03 modules.seriomap
-rw-r--r--  1 root root 144737 2007-02-16 00:03 modules.symbols
-rw-r--r--  1 root root 388977 2007-02-16 00:03 modules.usbmap
drwxr-xr-x  2 root root    380 2007-02-18 17:11 volatile


I'm new to linux. Please help.
Thanks in advance.

---

### Post by po0f on 2007-02-18
DesiSinger,

After installing "linux-headers-$(uname -r)" you should be fine:

```
[FONT="Courier New"]
$ sudo apt-get install linux-headers-$(uname -r)[/FONT]
```

---

### Post by DesiSinger on 2007-02-19
Thanks a lot.
That did help.
:guitar:

---

