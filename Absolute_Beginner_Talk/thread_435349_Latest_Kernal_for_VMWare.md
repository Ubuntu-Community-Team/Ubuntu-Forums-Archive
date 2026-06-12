---
title: "Latest Kernal for VMWare?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-05-06
I have Fiesty and couldn't get the VMWare server to install when I last tried, about a month ago.  It basically said the Kernal wasn't supported.  Where can I find the latest Kernal that VMWare supports?

---

### Post by Bachstelze on 2007-05-06
First, it' a kern**el**l.

Have you tried the latest vmware server (1.0.3) ? Maybe it supports 2.6.20 kernels...

---

### Post by JNowka on 2007-05-06
I don't know if it is the latest but you can use Canonicals commercial repository to install VMware server.  Just add this to your sources.list file.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

---

### Post by kc5hwb on 2007-05-06
Actually I just found that this install worked on the Terminal

```
sudo aptitude install vmware-server-kernel-modules-2.6.20-15
```

---

### Post by kc5hwb on 2007-05-06
> **HymnToLife said:**
> First, it' a kern**el**l.

Have you tried the latest vmware server (1.0.3) ? Maybe it supports 2.6.20 kernels...

Excuse my spelling problems, I am seeking counseling for that.

And yes I am using the latest server.

---

### Post by Bachstelze on 2007-05-06
Then I guess what you did was the easiest way to go. Is it working now ?

---

### Post by kc5hwb on 2007-05-06
> **HymnToLife said:**
> Then I guess what you did was the easiest way to go. Is it working now ?

Well, it installed fine... but it doesn't launch now.  I choose the vmware option from the Apps menu, it opens as though it is minimized on the bottom of the screen, and after about 30 seconds it disappears and no window ever opens.

---

### Post by Opsidian on 2007-05-07
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Works great.

---

### Post by kc5hwb on 2007-05-07
> **Opsidian said:**
> [http://www.virtualbox.org/](http://www.virtualbox.org/)

Works great.

Nope....it doesn't.  I tried that originally after I found that VMWare wouldn't support my Kernel.  It installed fine, setup and opened fine...seemed to install Windows XP ok, but then upon copying files to the HDD, it freezes and reboots the machine.  I tried this 3 times.  Never could get XP to install using VB.

---

### Post by kc5hwb on 2007-05-07
I downloaded the latest version again, 1.0.3 and started over.  I am getting the SAME error I have always had when trying to install VMWare on Fiesty...

```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

---

### Post by Bachstelze on 2007-05-07
Yep, this is a well know isuue, there's a patch out there for it. Could you please tell me as precisely as possible what you've done so far so I can tell you how to install it ?

---

### Post by kc5hwb on 2007-05-07
The any-any patch?  I tried that also.

I followed these instructions.
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

For some reason now, VirtualBox is working.  I guess the 5th time is the charm.  I was able to get XP installed and up and running fine.  So I think this is going to work for me.  I would still like to try VMware, VB seems to not want to let go of my mouse...and when I get it to, it reboots the whole machine.

---

