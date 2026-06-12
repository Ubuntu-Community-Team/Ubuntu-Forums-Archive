---
title: "can't install hcfusbmodem under edgy"
date: 2006-12-18
forum: Apple PPC Users
---

### Post by coiske on 2006-12-18
I can't install the Linuxant driver for Apple's USB modem on my Edgy PowerBook G4.  I downloaded the hcfusbmodem driver, did a make install, and ran hcfusbconfig.

Make install only gave me one error ("WARNING: Trying to compile kernel modules on an unknown system while the installed hcfusb driver package is for powerpc, this is likely to fail.)  It seemed to work, though.

However, hcfusbconfig failed to build the kernel modules.  Inspecting hcfusbconfig-buildlog.txt, I noticed three types of errors: the unknown system error, FILEIDNUM is not defined in several header files, and there is no such file as asm/suspend.h .

I checked, and the appropriate kernel header packages (linux-headers-2.6.17-10 and linux-headers-2.6.17-10-powerpc) are installed.  Any suggestions on what I could try to get this working?

---

### Post by BryannMelvin on 2007-03-05
I realize this is a VERY late reply: I found this unanswered post googling for info on this problem.

having the same problem, I compiled a kernel from sources. Twice. Once using Ubuntu sources for dapper 2.6.15 once using 2.6.20 from kernel.org.

This solves the problem of building the modules. There is a secondary problem of the driver not finding the modem.

I will post something when I have had time to look at this further. This is not an edgy specific problem.

Linuxant support is quite useless concerning this. They have a pat answer that debian kernel sources configuration is the problem. 

FWIW you can compile a kernel with NO CHANGES to config and the modules will build. I haven't tracked down the difference. Probably related to the linux link one would place in /usr/src to the sources one is using to build with.

Like I said in my experiments even though I got the modules to build I still didn't get the modem working.

Bryann

---

