---
title: "VMware config"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-03-10
I have just installed vmware workstation and now i am trying to run the configure process to get it running. When i run ```
sudo vmware-config.pl
```

I get this error:

[I]Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-9-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-9-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-9-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.
[/I]


Any ideas on how to fix this? Also i have tried with the 2.6.20-5 kernel instead of 2.6.20-9 but still not luck. Is the 2.6.20 series of kernels for ubuntu not compatible?
p.s  this is when it can't find a vmmon file for my kernel so i get it to compile one with gcc.

---

### Post by Bachstelze on 2007-03-10
Yes, VMware is not compatible wth 2.6.19+ kernels. There are patches to fix that though I've only tried them on VMware Server so I'm not 100% sure they'll work on Workstation. First, *cd* to the root of your extracted vmware tarball :

```
mfb@ana:~$ cd software/vmware/vmware-server-distrib/
```

Of course change the path to the directory to whatever is suitable for you. Then get the patch :

```
wget http://fkraiem.free.fr/vmmon.tar
sudo cp vmmon.tar lib/modules/source
```

And start the install script again :

```
sudo ./vmware-install.pl
```

---

### Post by ajmorris on 2007-03-10
> **HymnToLife said:**
> Yes, VMware is not compatible wth 2.6.19+ kernels. There are patches to fix that though I've only tried them on VMware Server so I'm not 100% sure they'll work on Workstation. First, *cd* to the root of your extracted vmware tarball :

```
mfb@ana:~$ cd software/vmware/vmware-server-distrib/
```

Of course change the path to the directory to whatever is suitable for you. Then get the patch :

```
wget http://fkraiem.free.fr/vmmon.tar
sudo cp vmmon.tar lib/modules/source
```

And start the install script again :

```
sudo ./vmware-install.pl
```

Works perfectly. Thank you so much!! :grin:

---

