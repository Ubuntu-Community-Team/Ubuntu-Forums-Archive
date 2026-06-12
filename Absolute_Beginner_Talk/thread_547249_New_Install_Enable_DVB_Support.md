---
title: "New Install Enable DVB Support"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by ddover on 2007-09-09
I just performed a new Fiesty install, I am very impressed with how far Ubuntu has come. Great work everyone.

I did this install to create a mythtv box.

I have two pchdtv 5500 cards which I beleive are supported natively by fiesty.

however when I do a ls /dev/dvb/ I get returns 
and when I do modprobe cx88_dvb I get errors

Any help would be very much appreciated.

Thanks!

---

### Post by ddover on 2007-09-09
Here is the error I get when trying to make install the card drivers

> danny@mediaserver:/tmp/v4l-dvb$ make
make -C /tmp/v4l-dvb/v4l 
make[1]: Entering directory `/tmp/v4l-dvb/v4l'
echo "No version yet."
No version yet.
uname -r|perl -ne 'if (/^([0-9]*)\.([0-9])*\.([0-9]*)(.*)$/) { printf ("VERSION=%s\nPATCHLEVEL:=%s\nSUBLEVEL:=%s\nKERNELRELEASE:=%s.%s.%s%s\n",$1,$2,$3,$1,$2,$3,$4); };' > ./.version
make[1]: Leaving directory `/tmp/v4l-dvb/v4l'
make[1]: Entering directory `/tmp/v4l-dvb/v4l'
scripts/make_makefile.pl
creating symbolic links...
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/tmp/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/v4l-dvb/v4l/flexcop-pci.o
In file included from /tmp/v4l-dvb/v4l/flexcop-pci.c:10:
/tmp/v4l-dvb/v4l/flexcop-common.h:11:26: error: linux/config.h: No such file or directory
In file included from /tmp/v4l-dvb/v4l/dmxdev.h:40,
                 from /tmp/v4l-dvb/v4l/flexcop-common.h:20,
                 from /tmp/v4l-dvb/v4l/flexcop-pci.c:10:
/tmp/v4l-dvb/v4l/dvbdev.h:30:35: error: linux/devfs_fs_kernel.h: No such file or directory
/tmp/v4l-dvb/v4l/flexcop-pci.c: In function 'flexcop_pci_irq_check_work':
/tmp/v4l-dvb/v4l/flexcop-pci.c:119: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/tmp/v4l-dvb/v4l/flexcop-pci.c: In function 'flexcop_pci_stream_control':
/tmp/v4l-dvb/v4l/flexcop-pci.c:222: warning: passing argument 1 of 'schedule_delayed_work' from incompatible pointer type
/tmp/v4l-dvb/v4l/flexcop-pci.c:225: warning: passing argument 1 of 'cancel_delayed_work' from incompatible pointer type
/tmp/v4l-dvb/v4l/flexcop-pci.c: In function 'flexcop_pci_init':
/tmp/v4l-dvb/v4l/flexcop-pci.c:300: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/tmp/v4l-dvb/v4l/flexcop-pci.c:379:71: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/tmp/v4l-dvb/v4l/flexcop-pci.c: In function 'flexcop_pci_probe':
/tmp/v4l-dvb/v4l/flexcop-pci.c:379: error: 'INIT_WORK' undeclared (first use in this function)
/tmp/v4l-dvb/v4l/flexcop-pci.c:379: error: (Each undeclared identifier is reported only once
/tmp/v4l-dvb/v4l/flexcop-pci.c:379: error: for each function it appears in.)
make[3]: *** [/tmp/v4l-dvb/v4l/flexcop-pci.o] Error 1
make[2]: *** [_module_/tmp/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/tmp/v4l-dvb/v4l'
make: *** [all] Error 2

---

### Post by gogan on 2007-09-11
As I know there is no support for kernel 2.6.20 or upper. I think you have already visited [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-3000). I have the same problem with an HVR 3000, the workaround is to get an old Kernel to compile properly although it's a bit tricky because metapackages in ubuntu. I have solved it with kernel from an old ubuntu's cd but now the problem is that I can't boot with it cos doesn't support my SATA controller

:(

Any help is highly appreciated!

---

### Post by ddover on 2007-09-11
I was unable to fix the problem directly but I did find a workaround of sorts. [http://www.mythbuntu.org/]("http://www.mythbuntu.org/") offers a mythtv system preconfigured to run on ubuntu. I d/led the alpha release 4 and have been VERY pleased with the results. It automatically detected all my hardware and run perfectly.  It really seems to me like it is a solid product. 

Good Luck

---

