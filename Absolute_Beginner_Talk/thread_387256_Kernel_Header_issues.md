---
title: "Kernel Header issues"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Paul_world10 on 2007-03-18
When I try to make a fresh NDIS Wrapper I continus to get kernal header errors. 

Heres whats I have:

root@desktopbox:/home/paul/ndiswrapper-1.38# ls -lh
total 60K
-rw-r--r-- 1 paul paul  116 2007-02-28 19:43 AUTHORS
-rw-r--r-- 1 paul paul  22K 2007-02-28 19:43 ChangeLog
drwxr-xr-x 2 paul paul 4.0K 2007-03-18 01:32 driver
-rw-r--r-- 1 paul paul 2.7K 2007-02-28 19:43 INSTALL
-rw-r--r-- 1 paul paul  881 2007-02-28 19:43 loadndisdriver.8
-rw-r--r-- 1 paul paul 2.7K 2007-02-28 19:43 Makefile
-rw-r--r-- 1 paul paul 3.4K 2007-02-28 19:43 ndiswrapper.8
-rw-r--r-- 1 paul paul 2.9K 2007-02-28 19:43 ndiswrapper.spec
-rw-r--r-- 1 paul paul 1.4K 2007-02-28 19:43 README
drwxr-xr-x 2 paul paul 4.0K 2007-02-28 19:43 utils
root@desktopbox:/home/paul/ndiswrapper-1.38# make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
root@desktopbox:/home/paul/ndiswrapper-1.38# make
make -C driver
make[1]: Entering directory `/home/paul/ndiswrapper-1.38/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/paul/ndiswrapper-1.38/driver'
make: *** [all] Error 2
root@desktopbox:/home/paul/ndiswrapper-1.38#




paul@desktopbox:~$ su
Password:
root@desktopbox:/home/paul# cd ..
root@desktopbox:/home# cd ..
root@desktopbox:/# cd /lib/modules
root@desktopbox:/lib/modules# ls -lh
total 32K
drwxr-xr-x 8 root root 4.0K 2006-12-30 16:08 2.6.15-23-386
drwxr-xr-x 3 root root 4.0K 2006-12-30 16:08 2.6.15-23-686
drwxr-xr-x 3 root root 4.0K 2006-12-30 16:08 2.6.15-23-k7
drwxr-xr-x 7 root root 4.0K 2006-12-17 05:19 2.6.15-26-386
drwxr-xr-x 8 root root 4.0K 2006-12-30 16:08 2.6.15-27-386
drwxr-xr-x 3 root root 4.0K 2006-12-30 15:51 2.6.15-27-686
drwxr-xr-x 3 root root 4.0K 2006-12-30 15:51 2.6.15-27-k7
drwxr-xr-x 7 root root 4.0K 2007-02-11 09:11 2.6.15-28-386
root@desktopbox:/lib/modules# cd 2.6.15-28-386
root@desktopbox:/lib/modules/2.6.15-28-386# ls -lah
total 1.5M
drwxr-xr-x  7 root root 4.0K 2007-02-11 09:11 .
drwxr-xr-x 10 root root 4.0K 2007-02-11 09:10 ..
drwxr-xr-x  2 root root 4.0K 2007-02-11 09:10 initrd
drwxr-xr-x 10 root root 4.0K 2007-02-11 09:10 kernel
drwxr-xr-x  2 root root 4.0K 2007-02-11 09:10 madwifi
drwxr-xr-x  2 root root 4.0K 2007-02-11 09:10 madwifi-ng
-rw-r--r--  1 root root 305K 2007-02-11 09:11 modules.alias
-rw-r--r--  1 root root   69 2007-02-11 09:11 modules.ccwmap
-rw-r--r--  1 root root 310K 2007-02-11 09:11 modules.dep
-rw-r--r--  1 root root  813 2007-02-11 09:11 modules.ieee1394map
-rw-r--r--  1 root root  806 2007-02-11 09:11 modules.inputmap
-rw-r--r--  1 root root  22K 2007-02-11 09:11 modules.isapnpmap
-rw-r--r--  1 root root   74 2007-02-11 09:11 modules.ofmap
-rw-r--r--  1 root root 246K 2007-02-11 09:11 modules.pcimap
-rw-r--r--  1 root root 1.2K 2007-02-11 09:11 modules.seriomap
-rw-r--r--  1 root root 138K 2007-02-11 09:11 modules.symbols
-rw-r--r--  1 root root 355K 2007-02-11 09:11 modules.usbmap
drwxr-xr-x  2 root root  440 2007-03-18 00:23 volatile
root@desktopbox:/lib/modules/2.6.15-28-386# cd kernel
root@desktopbox:/lib/modules/2.6.15-28-386/kernel# ls -lah
total 40K
drwxr-xr-x 10 root root 4.0K 2007-02-11 09:10 .
drwxr-xr-x  7 root root 4.0K 2007-02-11 09:11 ..
drwxr-xr-x  3 root root 4.0K 2007-02-11 09:10 arch
drwxr-xr-x  2 root root 4.0K 2007-02-11 09:10 crypto
drwxr-xr-x 35 root root 4.0K 2007-02-11 09:10 drivers
drwxr-xr-x 50 root root 4.0K 2007-02-11 09:10 fs
drwxr-xr-x  4 root root 4.0K 2007-02-11 09:10 lib
drwxr-xr-x 32 root root 4.0K 2007-02-11 09:10 net
drwxr-xr-x  2 root root 4.0K 2007-02-11 09:10 security
drwxr-xr-x 12 root root 4.0K 2007-02-11 09:10 sound
root@desktopbox:/lib/modules/2.6.15-28-386/kernel#


If anyone could help

---

### Post by yabbadabbadont on 2007-03-18
Try ```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by Paul_world10 on 2007-03-18
Thanks for your reply though I have entered the ```
sudo apt-get install linux-headers-`uname -r`
```  I guess I am supposed to be looking in  my   /lib/modules/latest kernel headers or whatnot for a  .conf   file of some sort which doesnt seem to be there. Oh well its just a bummer to not be able to compile anything.

---

