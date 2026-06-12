---
title: "Kernelpath"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Ephilei on 2006-07-08
When comiling Madwifi code into a driver, I run into this error:

> /bin/sh: line 0: cd: /lib/modules/2.6.12-9-386/build: No such file or directory
Makefile.inc:95: *** /lib/modules/2.6.12-9-386/build is missing, please set KERNELPATH.  Stop.

Does it want the kernel source code? I never compiled the kernel, just installed from a CD recently. The contents of /lib/modules/2.6.12-9-386/ are 
> 
initrd   modules.alias   modules.ieee1394map  modules.pcimap    modules.usbmap
kernel   modules.ccwmap  modules.inputmap     modules.seriomap  volatile
madwifi  modules.dep     modules.isapnpmap    modules.symbols

---

