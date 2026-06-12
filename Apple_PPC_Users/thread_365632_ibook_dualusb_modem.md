---
title: "ibook dualusb modem"
date: 2007-02-19
forum: Apple PPC Users
---

### Post by BryannMelvin on 2007-02-19
I am TRYING to compile the modem driver (linuxant) for my ibook G3 500
Using LTS

latest kernel has been tried and all kernels since -23

keep checking set up...have all sources and kernel sources.
Linuxant is not much help...they tell me the sources in ubuntu are the fault

[INDENT]
[/INDENT][INDENT]Hi,
 
the source of the problem is the following error message:
 
---
In file included from /usr/lib/hcfusbmodem/modules/osservices.c:29:
include/linux/suspend.h:5:25: error: asm/suspend.h: No such file or directory
---
 
I doubt that the source of the problem is the driver. Since the problem is that a kernel header tries to include another one and it fails, I suspect that the kernel headers package was not correctly packaged, which seems to happen from time to time on Debian based systems.
 
It is quite possible that the '/lib/modules/2.6.15-28-powerpc/build/include/asm' symlink is missing on your system or the whole kernel source tree is not properly configured to build kernel modules.
 
You could try with a fresh kernel from [http://www.kernel.org](http://www.kernel.org) to see if there is a difference.
 
Regards,
 
 
Jonathan
Technical specialist / Linuxant
[www.linuxant.com](www.linuxant.com)
[email]support@linuxant.com[/email]
 [/INDENT]


Has anyone any idead how to make this work.

?

bryann

---

