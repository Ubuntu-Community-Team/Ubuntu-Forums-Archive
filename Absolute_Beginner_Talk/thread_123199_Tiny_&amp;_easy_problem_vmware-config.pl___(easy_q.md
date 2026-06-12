---
title: "Tiny &amp; easy problem: vmware-config.pl   (easy question)"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-01-29
I have a problem with my vmware.. .please could you let me know what to do to make work
the vmware-config.pl
(strange cos everthg is normally right I guess, no ?)
 
Please could you have a quick look at the last line of the code below 
   
  
Thank you very much of your help

Patrick

```

# export CC=/usr/bin/gcc-3.4
 vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.12-9-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.12-9-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config4/vmmon-only/linux/hostif.c:68:
/tmp/vmware-config4/vmmon-only/./include/pgtbl.h: In function `PgtblVa2PTELocked':
/tmp/vmware-config4/vmmon-only/./include/pgtbl.h:81: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
  CC [M]  /tmp/vmware-config4/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config4/vmmon-only/common/vmx86.o
  LD [M]  /tmp/vmware-config4/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config4/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config4/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove it.
Somebody else apparently did it already.

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmnet-only'
make -C /lib/modules/2.6.12-9-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config4/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config4/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config4/vmnet-only/userif.o
In file included from /tmp/vmware-config4/vmnet-only/userif.c:45:
/tmp/vmware-config4/vmnet-only/pgtbl.h: In function `PgtblVa2PTELocked':
/tmp/vmware-config4/vmnet-only/pgtbl.h:81: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
/tmp/vmware-config4/vmnet-only/userif.c: In function `VNetUserIfMapUint32Ptr':
/tmp/vmware-config4/vmnet-only/userif.c:156: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/tmp/vmware-config4/vmnet-only/userif.c:157: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/tmp/vmware-config4/vmnet-only/userif.c: In function `VNetCopyDatagramToUser':
/tmp/vmware-config4/vmnet-only/userif.c:563: warning: implicit declaration of function `skb_copy_datagram'
  CC [M]  /tmp/vmware-config4/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config4/vmnet-only/bridge.o
/tmp/vmware-config4/vmnet-only/bridge.c: In function `VNetBridgeUp':
/tmp/vmware-config4/vmnet-only/bridge.c:586: warning: passing arg 3 of `sk_alloc' makes pointer from integer without a cast
/tmp/vmware-config4/vmnet-only/bridge.c:586: warning: passing arg 4 of `sk_alloc' makes integer from pointer without a cast
  CC [M]  /tmp/vmware-config4/vmnet-only/procfs.o
  LD [M]  /tmp/vmware-config4/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
Warning: could not open /tmp/vmware-config4/vmnet-only/includeCheck.h: Invalid argument
*** Warning: "skb_copy_datagram" [/tmp/vmware-config4/vmnet-only/vmnet.ko] undefined!
  CC      /tmp/vmware-config4/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config4/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config4/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config4/vmnet.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by patrick295767 on 2006-01-29
(additionally my breezy kernel was said to be compiled with gcc 3.4.5
I installed : 
apt-get -f install gcc-3.4 
Is it sufficient ?
  
.... 
Thank you

---

### Post by MartinG on 2006-01-29
Which version of VMWare are you running? If less than 5.5 then the first thing I'd try is to update to the latest version, 5.5.1. Updates from 5.0 are free.
 
 If you're using 4.5 or earlier, or the above doesn't work, then try this (no guarantees):
 Remove VMWare, then download the latest any-any patch ([http://ftp.cvut.cz/vmware/vmware-any...date96.tar.gz)](http://ftp.cvut.cz/vmware/vmware-any...date96.tar.gz)), then re-install vmware using the patch.
 
 (to do this, run the patch "runme.pl" before running vmware.config.pl).

You're fine with the compiler -- you wouldn't have got as far as you did otherwise:)

EDIT:
Sorry, the above is a bit misleading.  You need VMWare installed, but not configured, when you run the patch's runme.pl.

---

### Post by firetux on 2006-01-29
look [here]("http://www.ubuntuforums.org/showthread.php?t=77040&highlight=vmware")

Its the same problem I had, the second post in that topic holds the solution.

---

### Post by patrick295767 on 2006-01-29
[QUOTE=MartinG]Which version of VMWare are you running? If less than 5.5 then the first thing I'd try is to update to the latest version, 5.5.1. Updates from 5.0 are free.
 
 If you're using 4.5 or earlier, or the above doesn't work, then try this (no guarantees):
 Remove VMWare, then download the latest any-any patch ([http://ftp.cvut.cz/vmware/vmware-any...date96.tar.gz)](http://ftp.cvut.cz/vmware/vmware-any...date96.tar.gz)), then re-install vmware using the patch.
 
 (to do this, run the patch "runme.pl" before running vmware.config.pl).

You're fine with the compiler -- you wouldn't have got as far as you did otherwise:)

EDIT:
Sorry, the above is a bit misleading.  You need VMWare installed, but not configured, when you run the patch's runme.pl.[/QUOTE]

My  
Version: 4.5.2-8848
 
I'll try tomorrow 

Thank you again & very much !

Pat'

---

