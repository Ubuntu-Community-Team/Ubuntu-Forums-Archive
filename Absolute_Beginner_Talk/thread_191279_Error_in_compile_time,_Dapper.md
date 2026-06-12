---
title: "Error in compile time, Dapper"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2006-06-07
I wanna compile a driver for my sound card, but errors occured:
```
make[1]: Entering directory `/home/neo/riptide-0.6lnxtbeta03122800/scripts'
install -m 755 ripconfig ripstop /usr/sbin
make[1]: Leaving directory `/home/neo/riptide-0.6lnxtbeta03122800/scripts'
make[1]: Entering directory `/home/neo/riptide-0.6lnxtbeta03122800/modules'
common.mak:11: *** Is the kernel-source package installed? KERNELSRC does not point to a proper directory (/lib/modules/2.6.15-23-386/build). Stop.
make[1]: Leaving directory `/home/neo/riptide-0.6lnxtbeta03122800/modules'
make: *** [install] Error 2

```

---

### Post by Dr. Nick on 2006-06-07
Install the linux-source package for your kernel.

run from a terminal
 uname -r
to see you kernel version then isntall the approite source

---

