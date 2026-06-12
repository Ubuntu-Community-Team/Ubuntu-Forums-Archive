---
title: "Trouble Installing Ndiswrapper"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by mike3fresh on 2005-08-04
i'm trying to set up my wireless card (wg111 v2) in ubuntu, and i have heard a lot about ndiswrapper, so i downloaded it and un-tarred it. When i try to make, i get the message

[B]make -C driver
make[1]: Entering directory `/home/admin/ndiswrapper-1.2-rc1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-k7/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/admin/ndiswrapper-1.2-rc1/driver'
make: *** [all] Error 2
admin@ubuntu:~/ndiswrapper-1.2-rc1$[/B]

so as i checked that shortcut "build" i got an error message saying


[B]This link can't be used, because its target "/usr/src/linux-2.6.10-5-k7" doesn't exist.
[/B]

So i checked that folder, and in usr\src\, the only folder there is called "rpm"

i have also tried installing the headers, but that did not work either, so if someone could help me out, i would greatly appreciate it

---

