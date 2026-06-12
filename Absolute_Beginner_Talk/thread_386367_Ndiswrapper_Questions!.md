---
title: "Ndiswrapper Questions!"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by derryk on 2007-03-16
[B]okay, so I'm trying to get my wireless usb internet adapter to work in ubuntu (6.06)... but ndiswrapper is giving me grief. I've followed numberous step-by-step instructions on how to do it, but it just doesn't seem to work. Lets start from the beginning.

- first i made sure that i have the ndiswrapper utilities installed (under system/administration/synaptec package manager) ... ok
- then i downloaded the newest version of ndiswrapper and un tar'd it using the terminal and browsed to the directory (ndiswrapper-1.38) afterwards
- then i did a "make distclean" ... seems to of worked fine, nothing looks out of order. here is what it said, just for fun's sake:[/B]

derryk@derryk-desktop:~/ndiswrapper-1.38$ make distclean
make -C driver clean
make[1]: Entering directory `/home/derryk/ndiswrapper-1.38/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoske rnel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapp er.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
make[1]: Leaving directory `/home/derryk/ndiswrapper-1.38/driver'
make -C utils clean
make[1]: Entering directory `/home/derryk/ndiswrapper-1.38/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/derryk/ndiswrapper-1.38/utils'
rm -f *~
rm -fr ndiswrapper-1.38 ndiswrapper-1.38.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/derryk/ndiswrapper-1.38/driver'
rm -rf ndiswrapper.ko ndiswrapper.o crt.o hal.o iw_ndis.o loader.o ndis.o ntoske rnel.o ntoskernel_io.o pe_linker.o pnp.o proc.o rtl.o wrapmem.o wrapndis.o wrapp er.o divdi3.o usb.o win2lin_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions Modules.symvers Module.symvers
rm -f *_exports.h .\#* win2lin_stubs.h
make[1]: Leaving directory `/home/derryk/ndiswrapper-1.38/driver'
make -C utils distclean
make[1]: Entering directory `/home/derryk/ndiswrapper-1.38/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/derryk/ndiswrapper-1.38/utils'
rm -f .\#*

**- then i did a "make" but it has the following error:**

derryk@derryk-desktop:~/ndiswrapper-1.38$ make
make -C driver
make[1]: Entering directory `/home/derryk/ndiswrapper-1.38/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/derryk/ndiswrapper-1.38/driver'
make: *** [all] Error 2

[B]- thought nothing of it, although it looks strange.
- next i did a "sudo make install" but it gave me the following error:[/B]

derryk@derryk-desktop:~/ndiswrapper-1.38$ sudo make install
make -C driver install
make[1]: Entering directory `/home/derryk/ndiswrapper-1.38/driver'
Can't find kernel build files in /lib/modules/2.6.15-28-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/derryk/ndiswrapper-1.38/driver'
make: *** [install] Error 2
[B]
- well, looks pretty much like the same error i recieved when doing "make" now that i look closer. okay, any ideas people?[/B]

---

### Post by K.Mandla on 2007-03-16
:-k ... The first question that comes to mind is, do you need to install ndiswrapper over top of the one you installed at first? I believe the ndiswrapper-utils you're installing with 6.06 is [1.8]("http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils"). Does 1.38 have some particular function you need?

By the way, what kind of wireless card are you using?

---

