---
title: "kernel path for installing ndiswrapper"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by ladyinred on 2007-06-22
I am trying to get my wireless card to work, and all the documentation I've seen for the Broadcom bcm94318 card says to use ndiswrapper. However, I can't get it to compile:

rcox@ladyinred:~/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/rcox/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/rcox/ndiswrapper-1.47/driver'
make: *** [all] Error 2

I don't know enough to troubleshoot this error. I'm running Dapper Drake, if that helps any.

---

### Post by Alex Spencer on 2007-06-22
Is the '9' supposed to be there? Are you sure it isn't a bcm43xx wireless card? If so...search for bcm43xx on google...there is a tutorial which should help (you don't need to use ndiswrapper...you use fwcutter)

---

### Post by Alex Spencer on 2007-06-22
Here's that tutorial I was talking about:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

