---
title: "VMWare Install Error"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Squizz on 2007-12-13
I just tried to install VMWare server, using all of the default options, and this error cropped up:

```

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

simon@gutsy64si:~/vmware-server-distrib$ 

```

Any idea how I can fix it please?

Ta muchly :)

---

### Post by hfranco on 2007-12-13
I've installed VMWare with the following tutorial.

I'm sure this will help you out:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/CommercialApplications#Manual_install_.28optional.29_for_VMWare_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty/CommercialApplications#Manual_install_.28optional.29_for_VMWare_Server)

---

### Post by Squizz on 2007-12-13
The domain where the patches were hosted has since died :(

But patches seem to be the way forward, will see if I can find them elsewhere thanks.

---

### Post by hfranco on 2007-12-13
I've located the vmmon.tar and vmnet.tar files in my /usr/lib/vmware/modules/source directory.

I've uploaded them here:

vmmon.tar
[http://download.yousendit.com/FBCED5A13DD7ACE1](http://download.yousendit.com/FBCED5A13DD7ACE1) 

vmnet.tar
[http://download.yousendit.com/DD00856E679C6CA7](http://download.yousendit.com/DD00856E679C6CA7) 

These downloads are only good for 7 days.

Hopefully they work for you.

---

### Post by Squizz on 2007-12-13
```

The configuration of VMware Server 1.0.3 build-44356 for Linux for this running
kernel completed successfully.

```

That did the trick - thank you ever so much - you're a star :)

---

