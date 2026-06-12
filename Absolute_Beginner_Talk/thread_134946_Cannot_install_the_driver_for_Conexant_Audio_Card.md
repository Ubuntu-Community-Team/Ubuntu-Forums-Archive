---
title: "Cannot install the driver for Conexant Audio Card"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2006-02-22
I have downloaded the driver(RIP TIDE) from [www.linuxant.com](www.linuxant.com) for the Conexant Audio Card. But I cannot install it. Some errors occurs:
```
make[1]: Entering directory `/home/neo/riptide-0.6lnxtbeta03122800/scripts'
install -m 755 ripconfig ripstop /usr/sbin
make[1]: Leaving directory `/home/neo/riptide-0.6lnxtbeta03122800/scripts'
make[1]: Entering directory `/home/neo/riptide-0.6lnxtbeta03122800/modules'
common.mak:11: *** Is the kernel-source package installed? KERNELSRC does not point to a proper directory (/lib/modules/2.6.12-10-686/build).  Stop.
make[1]: Leaving directory `/home/neo/riptide-0.6lnxtbeta03122800/modules'
make: *** [install] Error 2
```
I have install the kernel-source package thru apt-get, but still cannot fix it.

---

