---
title: "Vmware server: help me please!"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by advilandy on 2007-03-12
I have been trying to get vmware server to work, and keep running into this during the install:

```
Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.17-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  SHIPPED /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
WARNING: could not find /tmp/vmware-config0/vmnet-only/.smac_linux.x386.o.cmd for /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vmnet.o': -1 File exists
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I have no idea why my kernel isn't okay or how to fix this (I saw something about the anyany patch but when I tried to run it it said not all of the vmware services could be stopped)

Please help!

---

### Post by advilandy on 2007-03-12
also, edgy kernel 2.6.17-11-generic

---

