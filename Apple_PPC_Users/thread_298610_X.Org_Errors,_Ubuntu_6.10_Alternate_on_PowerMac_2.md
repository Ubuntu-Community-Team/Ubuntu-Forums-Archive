---
title: "X.Org Errors, Ubuntu 6.10 Alternate on PowerMac 2"
date: 2006-11-13
forum: Apple PPC Users
---

### Post by MonkeyChewToy on 2006-11-13
I'm having some trouble getting Ubuntu to boot on my PowerMac 2. It starts up, and goes to a rather messed-up screen with the Ubuntu logo, in rainbow-colored photo negative style. Then, after attempting to load, it gives me the following errors. My firmware data is as follows:

Apple PowerMac2, 1 1.2f2 BootRom
9 September 1999

That was scrawled on a notecard a while back; I'm not sure of the actual parsing. And I don't know if that's the proper date format, either. I'd scrawled "9/9/99."

Anyway, the information and errors I receive are:

Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.17-9-powerpc64-smp ppc
Current Operating System: Linux iBuntu 2.6.17-10-powerpc #2 Fri Oct 13 16:37:41 UTC 2006 ppc
Build Date: 07 July 2006

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 1 03:21:02 1904
(==) Using config file: "/etc/X11/xorg.conf"
(WW) ****INVALID IO ALLOCATION**** b: 0xf00004000 e: 0xf00004ff
correcting^G
(EE) end of block range 0xefffffff < begin 0xf0000000
(EE) R128(0): mmap mmio: Invalid argument

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x98) [0x1008edfc]
1: [0x100374]
2: /usr/lib/xorg/modules/drivers/r128_drv.so [0xf7d23a8]
3: /usr/lib/xorg/modules/drivers/r128_drv.so(R128PreInit+0x6f0)
4: /usr/X11R6/bin/X(InitOutput+0xb28) [0x10064fe8]
5: /usr/X11R6/bin/X(main+0x290) [0x100253e4]
6: /lib/inc.so.6 [0xfc46728]
7: /lib/inc.so.6 [0xfc46978]

Fatal server error:
Caught Signal 11. Server aborting

iBuntu is my clever little name for my Ubuntu iMac. I'm sure I'm not the first. Anyway, when asked if I wanted to see further details, I hit OK and received this:

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  1 03:21:02 1904
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "iMac"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 RL/VR AGP"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) 'fonts.dir' not found (or not valid) in
"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on
"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").

I don't know if that has anything to do with anything. After that bit was a good deal of (II), (==), and (**) markers, concluded by the same errors as presented by the first "OK" hit.

I'd very much appreciate a way to resolve this, as I'm looking forward to having my very own Ubuntu server. Thanks in advance for any help you can give me.

---

