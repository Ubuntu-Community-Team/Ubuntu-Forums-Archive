---
title: "Rebuilding r8168-dkms"
date: 2015-02-11
forum: Apple Hardware Users
---

### Post by AnrDaemon on 2015-02-11
I'm trying to rebuild r8168-dkms with a newer source from Realtek for 12.04.
Changed the package and built the deb just fine, but when trying to install…
```
# dpkg -i r8168-dkms_8.039.00-0private_all.deb
Selecting previously unselected package r8168-dkms.
(Reading database ... 155311 files and directories currently installed.)
Unpacking r8168-dkms (from r8168-dkms_8.039.00-0private_all.deb) ...
Setting up r8168-dkms (8.039.00-0private) ...
Loading new r8168-8.039.00 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-45-generic
Building for architecture i686
Building initial module for 3.13.0-45-generic
Error! Bad return status for module build on kernel: 3.13.0-45-generic (i686)
Consult /var/lib/dkms/r8168/8.039.00/build/make.log for more information.

# cat /var/lib/dkms/r8168/8.039.00/build/make.log
DKMS make.log for r8168-8.039.00 for kernel 3.13.0-45-generic (i686)
Wed Feb 11 16:38:33 MSK 2015
make -C src/ clean
make[1]: Entering directory `/var/lib/dkms/r8168/8.039.00/build/src'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/var/lib/dkms/r8168/8.039.00/build/src'
make: *** [clean] Error 2
```

That doesn't make any sense whatsoever.
The target "clean" is obviously in there.
Moreover, when I enter the dir and rerun make by hands, it all work:
```
# cd /var/lib/dkms/r8168/8.039.00/build
# make
make -C src/ clean
make[1]: Entering directory `/var/lib/dkms/r8168/8.039.00/build/src'
make -C /lib/modules/3.13.0-45-generic/build SUBDIRS=/var/lib/dkms/r8168/8.039.00/build/src clean
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-45-generic'
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-45-generic'
make[1]: Leaving directory `/var/lib/dkms/r8168/8.039.00/build/src'
make -C src/ modules
make[1]: Entering directory `/var/lib/dkms/r8168/8.039.00/build/src'
make -C /lib/modules/3.13.0-45-generic/build SUBDIRS=/var/lib/dkms/r8168/8.039.00/build/src modules
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-45-generic'
  CC [M]  /var/lib/dkms/r8168/8.039.00/build/src/r8168_n.o
  CC [M]  /var/lib/dkms/r8168/8.039.00/build/src/r8168_asf.o
  CC [M]  /var/lib/dkms/r8168/8.039.00/build/src/rtl_eeprom.o
  CC [M]  /var/lib/dkms/r8168/8.039.00/build/src/rtltool.o
  LD [M]  /var/lib/dkms/r8168/8.039.00/build/src/r8168.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /var/lib/dkms/r8168/8.039.00/build/src/r8168.mod.o
  LD [M]  /var/lib/dkms/r8168/8.039.00/build/src/r8168.ko
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-45-generic'
make[1]: Leaving directory `/var/lib/dkms/r8168/8.039.00/build/src'
make -C src/ install
make[1]: Entering directory `/var/lib/dkms/r8168/8.039.00/build/src'
make -C /lib/modules/3.13.0-45-generic/build SUBDIRS=/var/lib/dkms/r8168/8.039.00/build/src INSTALL_MOD_DIR=kernel/drivers/net/ethernet/realtek modules_install
make[2]: Entering directory `/usr/src/linux-headers-3.13.0-45-generic'
  INSTALL /var/lib/dkms/r8168/8.039.00/build/src/r8168.ko
Can't read private key
  DEPMOD  3.13.0-45-generic
make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-45-generic'
make[1]: Leaving directory `/var/lib/dkms/r8168/8.039.00/build/src'
```

The question is… what I'm doing wrong?
More important question - how to get it right?

---

### Post by AnrDaemon on 2015-02-14
crickets&#8230;

---

