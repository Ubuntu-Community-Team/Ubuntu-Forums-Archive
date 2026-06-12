---
title: "Trying to get Broadcom 4318 working...  kerne build file missing?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Tagged on 2006-12-30
I have tried a few times by differant posts to get my broadcom 4318 airbus card working on my Compaq Presario V2565 us without success. (AMD64 Turion, with Ubuntu Edgy 6.10 64 iso install)

On my latest attempt I am trying to follow this post [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

I am on Step 5 - Extract and install the ndiswrapper using make

Here is my output, looks like my kernel build file is not there?  Any help?  I would LOVE to get online!

```
me@me:~/ndiswrapper-1.28$ make distclean
make -C driver clean
make[1]: Entering directory `/home/me/ndiswrapper-1.28/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/me/ndiswrapper-1.28/driver'
make -C utils clean
make[1]: Entering directory `/home/me/ndiswrapper-1.28/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/me/ndiswrapper-1.28/utils'
rm -f *~
rm -fr ndiswrapper-1.28 ndiswrapper-1.28.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/me/ndiswrapper-1.28/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h
make[1]: Leaving directory `/home/me/ndiswrapper-1.28/driver'
make -C utils distclean
make[1]: Entering directory `/home/me/ndiswrapper-1.28/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/me/ndiswrapper-1.28/utils'
rm -f .\#*
me@me:~/ndiswrapper-1.28$ make
make -C driver
make[1]: Entering directory `/home/me/ndiswrapper-1.28/driver'
Can't find kernel build files in /lib/modules/2.6.19.1/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/me/ndiswrapper-1.28/driver'
make: *** [all] Error 2
me@me:~/ndiswrapper-1.28$ sudo make install
make -C driver install
make[1]: Entering directory `/home/me/ndiswrapper-1.28/driver'
Can't find kernel build files in /lib/modules/2.6.19.1/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/me/ndiswrapper-1.28/driver'
make: *** [install] Error 2

```

---

### Post by teaker1s on 2006-12-30
have you 
You will need to install the essential build files to compile the driver:

user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

---

### Post by Tagged on 2006-12-30
Did that already but did it again with the following responce, 

```
me@me:~/ndiswrapper-1.28$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@me:~/ndiswrapper-1.28$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.19.1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@me:~/ndiswrapper-1.28$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
ln: creating symbolic link `/lib/modules/2.6.19.1/build' to `/usr/src/linux-2.6.19.1': File exists

```

then did step 5 again with the same message 
```
Entering directory `/home/me/ndiswrapper-1.28/driver'
Can't find kernel build files in /lib/modules/2.6.19.1/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/me/ndiswrapper-1.28/driver'
make: *** [all] Error 2

```

still at the same place.  Any other ideas?  And thanks for your help!

I am new to ubuntu and have it on my PC, would love to get my laptop online so i can get away from MS cept for games.

Thanks again!

---

