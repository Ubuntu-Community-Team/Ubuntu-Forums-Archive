---
title: "Trouble with VMware and kernel headers"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Ellidi on 2006-08-17
I know that there are several discussions on this subject but I didn't find anyone with the same problem as me. I aldready installed the correct kernel headers for my system ( linux-headers-2.6.15-26-386 ) but this is what happens when I run 'sudo vmware-config.pl':
```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /usr/src/linux-headers-2.6.15-26-386/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
Makefile:536: /usr/src/linux-headers-2.6.15-26-386/arch/i386/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.15-26-386/arch/i386/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Since I'm no expert, I just can't figure it out on my own.
Thanks in advance, Ellidi.

---

