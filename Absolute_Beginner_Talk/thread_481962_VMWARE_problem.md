---
title: "VMWARE problem"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-23
I'm having some problem installing vmware i get the following error. How do i solve it anyone?

> 
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:80:
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


---

### Post by ushills on 2007-06-23
In fiesty you can just install from applications>add / remove, search got vmware.

Then in synaptic chose the same version of vmware-tools.

You don't need to build it yourself.

Did this this morning and installed XP.

---

