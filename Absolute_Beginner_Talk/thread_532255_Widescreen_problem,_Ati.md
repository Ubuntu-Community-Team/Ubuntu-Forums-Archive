---
title: "Widescreen problem, Ati"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by japtar10101 on 2007-08-22
I'm attempting to make my ATI X1550 support Widescreen via Fiesty.  I've attempted one solution, but the X11 crashes:

> 1) I type in the terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

2) I press up until the highlight goes to Ati, then I press enter.

3) Here's where I get confused: It says, "select resolution", but some of them are already marked.  How do I mark a new resolution?  What I did instead was bring the highlight up to 1440x900 and pressed enter.

4) Logout, press ctrl+alt+backspace.  Crash.
So the question is, Am I doing something wrong here? Do I have to edit xorg.conf?  If so, in what way (using emacs)?

---

### Post by prince_niceguy on 2007-08-22
There will be a log created in the /var/log. Upload the same and some one should be able to help. The log name would be Xorg.**.log

---

### Post by .nedberg on 2007-08-22
> **japtar10101 said:**
> I'm attempting to make my ATI X1550 support Widescreen via Fiesty.  I've attempted one solution, but the X11 crashes:


So the question is, Am I doing something wrong here? Do I have to edit xorg.conf?  If so, in what way (using emacs)?

I think you add resolutins by pressing space, but I could be wrong. If you have to edit xorg.conf and don't know emacs I recomend nano, it is easier, but not as powerfull.

Oh, and remember to backup your xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working

---

### Post by Dave54 on 2007-08-22
Before reconfiguring your xorg, are you backing it up? If not, how are you recovering from the crash? To back up your xorg, use something like:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.08-22-07
```Then, if something bad happens, you can use the following to recover: ```
sudo cp /etc/X11/xorg.conf.backup.08-22-07 /etc/X11/xorg.conf
```

Next, try using the spacebar to select/deselect the resolutions.

Finally, if you can't make dpkg-reconfigure fix it, then we can modify your xorg manually.

Edit: Sorry for copying you nedberg, I began my post before you finished yours :p

---

### Post by japtar10101 on 2007-08-22
> **.nedberg said:**
> I think you add resolutins by pressing space, but I could be wrong. If you have to edit xorg.conf and don't know emacs I recomend nano, it is easier, but not as powerfull.

Oh, and remember to backup your xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working
My Comp Org teacher would torment me if I didn't know emacs:)!
I attempted space before, but I don't remember it having any particular effects.  I'll try it again tonight to see what I get.

> **Dave54 said:**
> Before reconfiguring your xorg, are you backing it up? If not, how are you recovering from the crash? To back up your xorg, use something like:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.08-22-07
```Then, if something bad happens, you can use the following to recover: ```
sudo cp /etc/X11/xorg.conf.backup.08-22-07 /etc/X11/xorg.conf
```

Next, try using the spacebar to select/deselect the resolutions.

Finally, if you can't make dpkg-reconfigure fix it, then we can modify your xorg manually.

Edit: Sorry for copying you nedberg, I began my post before you finished yours :p

Ugh, I had X11 crash on me so many times, I'm actually used to this now.  Actually, the above step automatically backs up for me, so it's really nice after I realized the X11 crashed.  Thanks though:)!

---

### Post by japtar10101 on 2007-08-22
Thanks for all your help, guys!  As you've said, the space bar DOES label chack marks.  That said, my problem is far from over...yes, sadly, this method crashed my X11 again for the 15th time (I didn't count).

Enter prince_niceguy:
> **prince_niceguy said:**
> There will be a log created in the /var/log. Upload the same and some one should be able to help. The log name would be Xorg.**.log

As such, I've attached two text files: one contains the settings that was generated from the dpkg-reconfigure in etc/X11/xorg.conf, and the other, the (hopefully) error filled log from /var/log/Xorg.0.log (split into two files because the whole log itself was too big to upload).

---

### Post by CDL-WarChilde on 2007-08-22
I have the same exact issue, ATi graphics with widescreen LCD.  

Here's a copy of the xorg.**.log file
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux warchilde-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 22 19:48:08 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5a33 card 103c,2a31 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:11:0: chip 1002,437a card 103c,2a31 rev 80 class 01,01,8f hdr 00
(II) PCI: 00:12:0: chip 1002,4379 card 103c,2a31 rev 80 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 103c,2a31 rev 80 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,2a31 rev 80 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,2a31 rev 80 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,2a31 rev 81 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,2a31 rev 80 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,437b card 103c,2a31 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 0000,0000 rev 80 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 80 class 06,04,01 hdr 81
(II) PCI: 01:05:0: chip 1002,5a61 card 103c,2a31 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:02:0: chip 125d,2898 card 148d,1062 rev 03 class 07,80,00 hdr 00
(II) PCI: 02:05:0: chip 10ec,8139 card 103c,2a31 rev 10 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[2] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc RC410 [Radeon Xpress 200] rev 0, Mem @ 0xd0000000/28, 0xfeaf0000/16, I/O @ 0xd000/8, BIOS @ 0xfeac0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe0000000 to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[1] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[2] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[3] -1	0	0xfe9fc000 - 0xfe9fcfff (0x1000) MX[B]
	[4] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[5] -1	0	0xfe9fe000 - 0xfe9fefff (0x1000) MX[B]
	[6] -1	0	0xfe9ff800 - 0xfe9ff9ff (0x200) MX[B]
	[7] -1	0	0xfe9ff000 - 0xfe9ff1ff (0x200) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[10] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[14] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[20] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[21] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[22] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[26] -1	0	0x00003000 - 0x00003003 (0x4) IX[B]
	[27] -1	0	0x00004000 - 0x00004007 (0x8) IX[B]
	[28] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[29] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[1] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[2] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[3] -1	0	0xfe9fc000 - 0xfe9fcfff (0x1000) MX[B]
	[4] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[5] -1	0	0xfe9fe000 - 0xfe9fefff (0x1000) MX[B]
	[6] -1	0	0xfe9ff800 - 0xfe9ff9ff (0x200) MX[B]
	[7] -1	0	0xfe9ff000 - 0xfe9ff1ff (0x200) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[10] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[14] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[20] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[21] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[22] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[25] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[26] -1	0	0x00003000 - 0x00003003 (0x4) IX[B]
	[27] -1	0	0x00004000 - 0x00004007 (0x8) IX[B]
	[28] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[29] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[5] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[6] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[7] -1	0	0xfe9fc000 - 0xfe9fcfff (0x1000) MX[B]
	[8] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[9] -1	0	0xfe9fe000 - 0xfe9fefff (0x1000) MX[B]
	[10] -1	0	0xfe9ff800 - 0xfe9ff9ff (0x200) MX[B]
	[11] -1	0	0xfe9ff000 - 0xfe9ff1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[14] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[26] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[27] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[28] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[32] -1	0	0x00003000 - 0x00003003 (0x4) IX[B]
	[33] -1	0	0x00004000 - 0x00004007 (0x8) IX[B]
	[34] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[35] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[36] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.39.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.39.4
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.393.1                  
(II) ATI Proprietary Linux Driver Build Date: Jul 20 2007 13:50:07
(--) Chipset Supported AMD Graphics Processor (0x5A61) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[5] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[6] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[7] -1	0	0xfe9fc000 - 0xfe9fcfff (0x1000) MX[B]
	[8] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[9] -1	0	0xfe9fe000 - 0xfe9fefff (0x1000) MX[B]
	[10] -1	0	0xfe9ff800 - 0xfe9ff9ff (0x200) MX[B]
	[11] -1	0	0xfe9ff000 - 0xfe9ff1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[14] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[26] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[27] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[28] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[30] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[31] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[32] -1	0	0x00003000 - 0x00003003 (0x4) IX[B]
	[33] -1	0	0x00004000 - 0x00004007 (0x8) IX[B]
	[34] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[35] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[36] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e4ab8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[5] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[6] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[7] -1	0	0xfe9fc000 - 0xfe9fcfff (0x1000) MX[B]
	[8] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[9] -1	0	0xfe9fe000 - 0xfe9fefff (0x1000) MX[B]
	[10] -1	0	0xfe9ff800 - 0xfe9ff9ff (0x200) MX[B]
	[11] -1	0	0xfe9ff000 - 0xfe9ff1ff (0x200) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[14] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[29] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[30] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[31] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[32] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[35] -1	0	0x00003000 - 0x00003003 (0x4) IX[B]
	[36] -1	0	0x00004000 - 0x00004007 (0x8) IX[B]
	[37] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[38] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[39] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI Radeon Xpress Series" (Chipset = 0x5a61)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x2a31)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfeaf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 65536 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON XPRESS 200 Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS4 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.39.4
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: PTS  Model: 770  Serial#: 16843009
(II) fglrx(0): Year: 2006  Week: 9
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 41  vert.: 26
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.636 redY: 0.349   greenX: 0.290 greenY: 0.584
(II) fglrx(0): blueX: 0.143 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
(II) fglrx(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  410 x 256 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 60  V max: 75 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) fglrx(0): Serial No: F0SD63010690U
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004293700701010101
(II) fglrx(0): 	0910010308291a78ead6a5a2594a9524
(II) fglrx(0): 	145054afcf0081809500950f01010101
(II) fglrx(0): 	0101010101019a29a0d0518422305098
(II) fglrx(0): 	36009a001100001c302a009851002a40
(II) fglrx(0): 	307013009a001100001e000000fd003c
(II) fglrx(0): 	4b1e500e000a202020202020000000ff
(II) fglrx(0): 	004630534436333031303639305500cd
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 301/266MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 21 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 0)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (410, 260) mm
(--) fglrx(0): DPI set to (63, 75)
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "720x576": 32.7 MHz (scaled from 0.0 MHz), 35.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   32.66  720 744 816 912  576 577 580 597 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(**) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[7] -1	0	0xfe9f8000 - 0xfe9fbfff (0x4000) MX[B]
	[8] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[9] -1	0	0xfe9fc000 - 0xfe9fcfff (0x1000) MX[B]
	[10] -1	0	0xfe9fd000 - 0xfe9fdfff (0x1000) MX[B]
	[11] -1	0	0xfe9fe000 - 0xfe9fefff (0x1000) MX[B]
	[12] -1	0	0xfe9ff800 - 0xfe9ff9ff (0x200) MX[B]
	[13] -1	0	0xfe9ff000 - 0xfe9ff1ff (0x200) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B](B)
	[16] -1	0	0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[32] -1	0	0x00007000 - 0x0000700f (0x10) IX[B]
	[33] -1	0	0x00008000 - 0x00008003 (0x4) IX[B]
	[34] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[35] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[37] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[38] -1	0	0x00003000 - 0x00003003 (0x4) IX[B]
	[39] -1	0	0x00004000 - 0x00004007 (0x8) IX[B]
	[40] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[41] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[42] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7f13000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.39.4
(II) fglrx(0):     Date: Jul 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.20-16-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 21.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] texture shared area handle = 0x00008000
(II) fglrx(0): shared FSAAScale=2
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x3c000000 FBMappedSize: 0x00501000
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,1281)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1024 x 513
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:5:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

---

### Post by CDL-WarChilde on 2007-08-23
I seem to have an issue understanding the "Restricted Driver" and how that function interacts with Ubuntu.

Turned restricted drivers off and now have widescreen resolution available.....after editing the xorg.conf file.

---

