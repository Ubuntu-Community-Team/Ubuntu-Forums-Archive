---
title: "Can't run Xwindow on Old world G3(9600 with G3)"
date: 2007-03-01
forum: Apple PPC Users
---

### Post by jmygeni on 2007-03-01
I can't run Xwindows on My G3 Oldworld MAC(9600 with Sonnet 300Mhz/1MB cache).

OS : Ubuntu 5.1 

Video Card : ATi Mach32(for mac)

monitor : 14" CRT(IBM compatible)

system : PowerMac 9600 / Sonnet G3 card 512MB RAM

Sonnet ATA66 Card

What should I do to make Xwindow Running?

and What is wrong with my system?




X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010180225 [email]root@adare.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.12 ppc [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-powerpc #1 Mon Oct 10 15:26:45 BST 2005 ppc
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-powerpc (buildd@adare) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 15:26:45 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  2 09:39:28 2007
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(WW) ATI(0): Unknown RAMDAC type 0x9A detected.
(EE) ATI(0): Linear aperture not available.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by ristosu on 2007-03-03
You did check "/var/log/Xorg.0.log"?

Anyway, the actual problem seems to be: (EE) ATI(0): Linear aperture not available.

There might be some options to be put into "/etc/X11/xorg.conf" (Section "Device") for avoiding using linear aperture. It depends on the "ati" driver.

Another possibility is to use driver "fbdev" that uses console frame buffer device.

---

