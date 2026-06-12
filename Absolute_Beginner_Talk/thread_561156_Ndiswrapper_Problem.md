---
title: "Ndiswrapper Problem"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Amivit on 2007-09-27
Hey ubuntuforums.org community :) I am having a problem with my wireless card built in my laptop.
Here is the situation,

Background: Freshly installed Ubuntu 7.04 x86, with everything upgraded with apt-get. Plus all default excludes got installed.  Downloaded ndiswrapper 1.48 and got this error when following the guide here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/")
```

owner@owner-laptop:~/Downloads/ndiswrapper-1.48/ndiswrapper-1.48$ make distcleanmake -C driver clean
make[1]: Entering directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm: cannot remove `.tmp_versions/ndiswrapper.mod': Permission denied
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make: *** [clean] Error 2
owner@owner-laptop:~/Downloads/ndiswrapper-1.48/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
rm: cannot remove `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver/.tmp_versions/ndiswrapper.mod': Permission denied
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make: *** [all] Error 2


```
Now what is causing this error?

---

### Post by Seisen on 2007-09-27
Do you have build essential installed, did you isntall the kernel source package?

---

### Post by Amivit on 2007-09-27
I am not sure, when I installed Ubuntu I just ran apt-get upgrade. But when it was finished I noticed 4 or 5 items that were excluded. One of them was definitely header something so I just installed them.

---

### Post by Amivit on 2007-09-27
Just installed build essential. New error log at install:
```

owner@owner-laptop:~/Downloads/ndiswrapper-1.48/ndiswrapper-1.48$ make distcleanmake -C driver clean
make[1]: Entering directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm: cannot remove `.tmp_versions/ndiswrapper.mod': Permission denied
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make: *** [clean] Error 2
owner@owner-laptop:~/Downloads/ndiswrapper-1.48/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
rm: cannot remove `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver/.tmp_versions/ndiswrapper.mod': Permission denied
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make: *** [all] Error 2


```

---

### Post by Amivit on 2007-09-27
Okay I dont know what I did, but ndiswrapper definitely works now.
But now I have a new problem. When I install the same driver that I used for
my BackTrack2 distribution, the blue light on my laptop doesent light up. But on backtrack2 the driver worked perfectly on ndiswrapper. What could be up with that? I got a Broadcom 4321

---

### Post by igknighted on 2007-09-27
> **Amivit said:**
> Just installed build essential. New error log at install:
```

owner@owner-laptop:~/Downloads/ndiswrapper-1.48/ndiswrapper-1.48$ make distcleanmake -C driver clean
make[1]: Entering directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd  compat.h \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm: cannot remove `.tmp_versions/ndiswrapper.mod': Permission denied
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make: *** [clean] Error 2
owner@owner-laptop:~/Downloads/ndiswrapper-1.48/ndiswrapper-1.48$ make
make -C driver
make[1]: Entering directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
rm: cannot remove `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver/.tmp_versions/ndiswrapper.mod': Permission denied
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/owner/Downloads/ndiswrapper-1.48/ndiswrapper-1.48/driver'
make: *** [all] Error 2


```

"rm: cannot remove `.tmp_versions/ndiswrapper.mod': Permission denied"

It looks like you are not the owner of these files perhaps?  Or they are in a spot where you must be root to edit them.

---

