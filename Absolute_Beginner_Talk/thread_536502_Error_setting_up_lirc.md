---
title: "Error setting up lirc"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by martynh on 2007-08-27
Hi All
I'm trying to set up an Ubuntu (Feisty) box for mythtv. Thus far I've hit a few snags but managed to overcome them by reading forums such as this :)
I'm having trouble getting lirc working with my remote however (it came with a Leadtek DTV-1000) , I have tried to follow this guide: [http://daniel.saunders.googlepages.com/howto.html#WinFastDTV1000RemoteControlWithMythTV]("http://daniel.saunders.googlepages.com/howto.html#WinFastDTV1000RemoteControlWithMythTV")

but when I try to do a make in the v4l-dvb folder I get the following:  [FONT="Courier New"]/usr/src/v4l-dvb/v4l/flexcop-pci.c* :378:71: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
[/FONT]

The full log was:

[FONT="Courier New"]martyn@martyn-htpc:/usr/src/v4l-dv* b$ sudo make
make -C /usr/src/v4l-dvb/v4l
make[1]: Entering directory `/usr/src/v4l-dvb/v4l'
creating symbolic links...
make -C /lib/modules/2.6.20-16-generic/bui* ld SUBDIRS=/usr/src/v4l-dvb/v4l modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-* generic'
CC [M] /usr/src/v4l-dvb/v4l/flexcop-pci.o*
/usr/src/v4l-dvb/v4l/flexcop-pci.c* : In function 'flexcop_pci_irq_check_work':
/usr/src/v4l-dvb/v4l/flexcop-pci.c* :119: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/usr/src/v4l-dvb/v4l/flexcop-pci.c* : In function 'flexcop_pci_stream_control':
/usr/src/v4l-dvb/v4l/flexcop-pci.c* :226: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/usr/src/v4l-dvb/v4l/flexcop-pci.c* :229: warning: passing argument 1 of 'cancel_delayed_work' from incompatible pointer type
/usr/src/v4l-dvb/v4l/flexcop-pci.c* :378:71: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/usr/src/v4l-dvb/v4l/flexcop-pci.c* : In function 'flexcop_pci_probe':
/usr/src/v4l-dvb/v4l/flexcop-pci.c* :378: error: 'INIT_WORK' undeclared (first use in this function)
/usr/src/v4l-dvb/v4l/flexcop-pci.c* :378: error: (Each undeclared identifier is reported only once
/usr/src/v4l-dvb/v4l/flexcop-pci.c* :378: error: for each function it appears in.)
make[3]: *** [ /usr/src/v4l-dvb/v4l/flexcop-pci.o* ] Error 1
make[2]: *** [_module_/usr/src/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-* generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/v4l-dvb/v4l'
make: *** [all] Error 2[/FONT]

Any ideas? :confused:

---

