---
title: "location of the directory of C header files?"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by Hallavej on 2005-11-06
I'm trying to install VMware. And I must answer this question:

"What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]"

If I hit enter I get this:

"The path "/usr/src/linux/include" is not an existing directory"

/usr/src is empty, and my guess is to install kernel-source and kernel-headers. But my kernel is: 2.6.12-9-amd64-generic, and I can't find those in the repositories. There is version 2.6.11 but no 2.6.12.

Any ideas?

---

### Post by mlomker on 2005-11-06
```

sudo apt-get install linux-headers-$(uname -r)

```

---

### Post by Hallavej on 2005-11-06
[QUOTE=mlomker]```

sudo apt-get install linux-headers-$(uname -r)

```[/QUOTE]

Thank you

Now I got a bit further, and got this error:

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.12-9-amd64-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.12-9-amd64-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
/tmp/vmware-config0/vmmon-only/linux/driver.c:33:25: asm/ioctl32.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function `register_ioctl32_handlers':
/tmp/vmware-config0/vmmon-only/linux/driver.c:222: warning: implicit declaration of function `register_ioctl32_conversion'
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function `unregister_ioctl32_handlers':
/tmp/vmware-config0/vmmon-only/linux/driver.c:248: warning: implicit declaration of function `unregister_ioctl32_conversion'
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-amd64-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


The url's doesnt really help so I'm lost again. Any new ideas.

---

### Post by Mustard on 2005-11-06
A question I would be asking is how well is vmware supported on amd64 kernel.  I don't know whether thats the right question though. :)

I'm not that familiar with anything but the most common of errors on ubuntu, having not attempted to build any applications myself.

---

### Post by mlomker on 2005-11-06
What version you are installing?  With 5.0 you need to apply the [any-any-update94]("ftp://platan.vc.cvut.cz/pub/vmware/") patch and at 5.5 you should have no problems.

---

### Post by Hallavej on 2005-11-07
[QUOTE=mlomker]What version you are installing?  With 5.0 you need to apply the [any-any-update94]("ftp://platan.vc.cvut.cz/pub/vmware/") patch and at 5.5 you should have no problems.[/QUOTE]

That was it. Thanks a lot.

---

### Post by shahjapan on 2007-10-29
VMWare Tools also gives a rpm package to install vmware tools.

so copy that rpm package and convert it to .deb package using alien.

to install alien on ubuntu.

sudo apt-get install alien

---

