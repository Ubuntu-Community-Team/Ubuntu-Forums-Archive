---
title: "libpng12 bug?"
date: 2005-02-13
forum: Apple PPC Users
---

### Post by trash on 2005-02-13
ok so before I file a bug report.. here's the story.

after installing mol I got the same errors as posted on the maconlinux mailing list, that point to a libpng problem...

Mac-on-Linux 0.9.70 [Aug 3 2004 16:18]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Removing stale lockfile /var/lock/mol-0
Running in PowerPC 7400 mode, 256 MB RAM
Timebase: 33.29 MHz, Bus: 133.16 MHz, Clock: 466 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
***** SIGNAL 11 [Segmentation fault] in thread main-thread *****
si_signo = 11, si_errno 0, si_code 00000001, si_addr 0xfef63f64
Last RVEC: 0x0 (0), last OSI: 0, mac_nip FFF00100
NIP 0x0fbc6568
***** Backtrace *****
7fffedf0: backtrace + 0x3c
7fffee10: signal_handler + 0x178
7fffee30: 0x0fd48b64
7fffee60: 0x7ffff1b8
7ffff4b0: 0x0fd43cbc
7ffff4d0: 0x0fbc4fcc
7ffff4f0: 0x0fef76bc
7ffff510: 0x0fef767c
7ffff530: 0x0fee1254
7ffff560: 0x0fee15e8
7ffff580: 0x0feee890
7ffff720: 0x0feee79c
7ffff750: create_x_picture + 0x1e8
7ffff860: x11_init + 0x25c
7ffff8d0: driver_mgr_init + 0xc0
7ffff8f0: ioports_init + 0x44
7ffff900: main + 0x18c
7ffff920: 0x0fb68100
7ffff960: 0x00000000
cleaning up...

maconlinux.org.. i was searching archive for x11.kbd... tells of a bug and a fix... [http://lists.maconlinux.org/piperma...ber/003504.html](http://lists.maconlinux.org/piperma...ber/003504.html)

"With the help of Jens and reading the Debian
bug #278921 it works again. Thank you very much Jens.
In that report of emails the web page to download the Debian packages"

libpng12-0_1.2.5.0-7_powerpc.deb
libpng12-dev_1.2.5.0-7_powerpc.deb
> bug #278921 it works again.

and a fix is posted here...
[http://lists.maconlinux.org/pipermail/mol-general/2004-November/003510.html](http://lists.maconlinux.org/pipermail/mol-general/2004-November/003510.html)

So seeing as there is a fix already do i need to file a bug report?

and How do I go about downgrading this package?

Thanks
sorry to have repeated this from another mol thread but it is a seperate issue and nobody else seems to have had this problem.

PS. I did search bugzillaUbuntu but didn't find anything.

---

