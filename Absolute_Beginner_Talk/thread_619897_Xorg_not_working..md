---
title: "Xorg not working."
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by arckeda on 2007-11-21
Hello, I am working my friends computer.  He does not have a gui.  When I ssh and type startx, I get:

root@Shoe:~# startx
xauth:  creating new authority file /root/.serverauth.8768

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Shoe 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 21 23:25:09 2007
(==) Using config file: "/etc/X11/xorg.conf"

Requesting insufficient memory window!: start: 0xfc900000 end: 0xfc9fffff size 0x8000000
(EE) Cannot find empty range to map base to
(EE) RADEON(0): Cannot read V_BIOS (3)
Requesting insufficient memory window!: start: 0xfc900000 end: 0xfc9fffff size 0x8000000
(EE) Cannot find empty range to map base to
(II) Module already built-in
(II) Module already built-in

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONPreInit+0xb04) [0xb7b722d4]
3: /usr/bin/X11/X(InitOutput+0x9a4) [0x80a8e54]
4: /usr/bin/X11/X(main+0x27b) [0x8076ceb]
5: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d40050]
6: /usr/bin/X11/X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 8.  Server aborting

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

It has a x200 graphics card and a sony monitor, when I change the driver for ati to vesa I get:

root@Shoe:~# startx
xauth:  creating new authority file /root/.serverauth.8799

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux Shoe 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 21 23:26:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) VESA: No matching Device section for instance (BusID PCI:2:1:0) found
Requesting insufficient memory window!: start: 0xfc900000 end: 0xfc9fffff size 0x8000000
(EE) Cannot find empty range to map base to
(EE) VESA(0): Cannot read V_BIOS (3)
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

     -ARCKEDA

---

### Post by arckeda on 2007-11-22
It also has a nividia card.  How can I detect it?

---

