---
title: "how can I use my live cd to reset my gamma for my laptop screen?"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-10-25
I was trying to make my laptop screen darker(I use kubuntu dapper but also have gnome desktop and live cd) since its too light for me and i assumed it was causing problems on my laptop b/c the screen kept bouncing....so i went into system and hardware monitor and then admin and reset my gamma from 2.0(i think) to 1.4 b/c the examples in the four boxes got darker at 1.4. it said x-something needed to reboot so i rebooted my pc. things started normally then after i logged in with with my username and password then typed sudo kdm then password(when i deactivated gdm few weeks back this additional step was added and i dont know y) it loaded a distorted splash login page. basically unreadable. with for images of the screen and whatever i try to open.

so I have two options, somehow move the 2 folders i really want to my xp partition via command line(dont know how) and then on the 26th just fresh install edgy and pray for the best.

or use live cd to fix the problem...i googled all over and saw a similar issue but it was for fedora but it was solved with a live cd.

how can i solve the distorted monitor with live cd please?

if thats not possible how can i move /home/maddbaron/desktop/screenplays to /media/hda4 via command line? for the reinstall?

Please help.

---

### Post by .t. on 2006-10-25
OK. Listen carefully.
Log in as usual. It doesn't matter if the splash screen (or even the whole screen, for that matter) is distorted, as you won't be using that screen.

Once you are logged in, press Ctrl+Alt+F1. This should take you to a virtual terminal. Log in there, and run "DISPLAY=:0 xgamma -gamma *<whatever you previous gamma was>*". Then, press Ctrl+Alt+F7 to get back to the X session. If it hasn't worked, try again: gamma values can be between 0.100 and 10.000. If it isn't a gamma problem, go back to the terminal and run "sudo dpkg-reconfigure xserver-xorg". This will completely reconfigure X to what it was like on initial installation.

---

### Post by maddbaron on 2006-10-25
> **.t. said:**
> OK. Listen carefully.
Log in as usual. It doesn't matter if the splash screen (or even the whole screen, for that matter) is distorted, as you won't be using that screen.

Once you are logged in, press Ctrl+Alt+F1. This should take you to a virtual terminal. Log in there, and run "DISPLAY=:0 xgamma -gamma *<whatever you previous gamma was>*". Then, press Ctrl+Alt+F7 to get back to the X session. If it hasn't worked, try again: gamma values can be between 0.100 and 10.000. If it isn't a gamma problem, go back to the terminal and run "sudo dpkg-reconfigure xserver-xorg". This will completely reconfigure X to what it was like on initial installation.

Thank you! I will try it in a few, question does the last option erase anything? I dont remember what my previous gamma was I think 2.0 but I am not certain. and by login u mean like after where or before where the splash screen should be?

---

### Post by .t. on 2006-10-25
If you want to save the previous X config, make a back-up of /etc/X11/xorg.conf. I'm not sure if dpkg-reconfigure does that automagically. "Log in as usual" means at the graphical screen that appears after the computer has first booted.

---

### Post by maddbaron on 2006-10-25
how can i make a backup? i'll be typing kind of blind only way is in my first login which is all text and command lineafter I enter my username and password right before i get to the kdm splash login screen. I have two login's an initial text/command line one then the splash login one. i figure i can save in the initial login right before i type sudo kdm then password. but how?

---

### Post by .t. on 2006-10-25
To make a backup: "cp /etc/X11/xorg.conf ~/"
To restore the backup: "sudo cp ~/xorg.conf /etc/X11"

I don't quite see what you're trying to get at in the rest of that post...

---

### Post by maddbaron on 2006-10-25
nevermind i was babbling thank you for the instructions. I am going to log out of windows now and do it. thank you.

---

### Post by maddbaron on 2006-10-25
I screwed it up I believe.

I did the sudo dkpg  code and it asked me a bunch of questions i knew nothing about so i left the defaults on except when it asked my laptop's video card...all i remember from a month ago was my card had a name called VESA...so i typed in VESA. 

then it asked more questions and when I went to type in sudo kdm it kept giving me the load screen u get after grub but no letters or words just the kubuntu letter logo and the dark blue dash underneath that is support to fill up to light blue as the modules load.

i rebooted after 20mins of waiting for the modules to load. things started normally i typed sudo kdm again same problem so rebooted again and typed sudo gdm and it went to a blue and grey screen with yes and no options and it asked me did i want to see my xorg output and detailed xorg output at the bottom of both it said 

fatal server error 

no screens found.

is there anyway to fix this with a live cd?

if not how can I copy my files located at:
home/maddbaron/desktop/screenplays  and home/maddbaron/mozillabaron and /home/maddbaron/.mozilla/.gaim/.opera to a storage media called /media/hda4 and hda2 in my windows partition respectively? 

I will just use windows until edgy comes out final and fresh install with that since eitherway I will have to redo my broadcom wireless might as well use the new o.s.

I am not good at command line please be explicitly clear on what I should type please.

---

### Post by .t. on 2006-10-25
What filesystem does your Windows partition use?

After running GDM, what does the text say? Post the /var/log/Xorg.0.log file if you can, and your /etc/X11/xorg.conf. I don't see how your gonna do that, considering you probably can't get to them from Windows, but try anyway!

---

### Post by maddbaron on 2006-10-25
my windows is fat32 i save all my important files to my xp usually after kubuntu went wild on me in july but i got lazy and didnt do it last night(d'oh). 

from kubuntu i am able to write to windows no problem and read files too i usually do so in konquerer though but there must be a command line way of doing that isnt there?

as for the log files, how do i save them so I can access them via windows? I am on my laptop using the xp paritition I would need instructions on how to save them to xp somehow. But the screen is still distorted except for the grey box that told "server error no screens found"  it said in the detailed xorg everything loaded normal but then the error came up and that was just gdm in kdm all i got was the kubuntu text logo and nothing else.

I'd really like to fix this but it is looking more and more like I will need to do a complete reinstall come tomorrow since I don't know some answers the Xorg configuration was asking me and I'd rather just let the system do it for me.

---

### Post by maddbaron on 2006-10-25
scratch all of that...i installed a program from 
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

and i can now see my linux files. I am in the process of copying EVERYTHING to dvd.

Here is the xorg.o

> 
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux baronnet 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 25 08:48:32 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "vesa"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0760 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0963 card 0000,0000 rev 25 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1025,0083 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:6: chip 1039,7013 card 1025,0083 rev a0 class 07,03,00 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1025,0083 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1025,0083 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1025,0083 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7002 card 1025,0083 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1025,0083 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 104c,ac50 card 2400,0000 rev 02 class 06,07,00 hdr 02
(II) PCI: 00:0b:0: chip 14e4,4318 card 1468,0312 rev 02 class 02,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1039,6330 card 1025,0083 rev 00 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe2100000 - 0xe21fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:6:0), (0,2,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[1] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x32000000 - 0x33ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x31ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter rev 0, Mem @ 0xe8000000/27, 0xe2100000/17, I/O @ 0xa000/7
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe1ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe2000000 - 0xe2001fff (0x2000) MX[B]
	[1] -1	0	0xe2005000 - 0xe2005fff (0x1000) MX[B]
	[2] -1	0	0xe2004000 - 0xe2004fff (0x1000) MX[B]
	[3] -1	0	0xe2003000 - 0xe2003fff (0x1000) MX[B]
	[4] -1	0	0xe2002000 - 0xe2002fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xe2100000 - 0xe211ffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[9] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[10] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[11] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[12] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[13] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[14] -1	0	0x00008100 - 0x0000811f (0x20) IX[B]
	[15] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe2000000 - 0xe2001fff (0x2000) MX[B]
	[1] -1	0	0xe2005000 - 0xe2005fff (0x1000) MX[B]
	[2] -1	0	0xe2004000 - 0xe2004fff (0x1000) MX[B]
	[3] -1	0	0xe2003000 - 0xe2003fff (0x1000) MX[B]
	[4] -1	0	0xe2002000 - 0xe2002fff (0x1000) MX[B]
	[5] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[6] -1	0	0xe2100000 - 0xe211ffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[9] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[10] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[11] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[12] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[13] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[14] -1	0	0x00008100 - 0x0000811f (0x20) IX[B]
	[15] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
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
	[4] -1	0	0xe2000000 - 0xe2001fff (0x2000) MX[B]
	[5] -1	0	0xe2005000 - 0xe2005fff (0x1000) MX[B]
	[6] -1	0	0xe2004000 - 0xe2004fff (0x1000) MX[B]
	[7] -1	0	0xe2003000 - 0xe2003fff (0x1000) MX[B]
	[8] -1	0	0xe2002000 - 0xe2002fff (0x1000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xe2100000 - 0xe211ffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[15] -1	0	0x00001c80 - 0x00001cff (0x80) IX[B]
	[16] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[17] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[18] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[19] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[20] -1	0	0x00008100 - 0x0000811f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(WW) VESA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found


---

### Post by Dr. Nick on 2006-10-25
the [COLOR=#0000df]**sudo dpkg-reconfigure xserver-xorg **[/COLOR]shouldnt hurt anything past the xorg.conf file.

Once you boot linux and log in at the command promt try to re-run that without starting kdm or gdm. Make sure you set the monitor up right and again try vesa drivers, vesa is a generic driver which works in most cases.

---

### Post by maddbaron on 2006-10-25
> **Dr. Nick said:**
> the [COLOR=#0000df]**sudo dpkg-reconfigure xserver-xorg **[/COLOR]shouldnt hurt anything past the xorg.conf file.

Once you boot linux and log in at the command promt try to re-run that without starting kdm or gdm. Make sure you set the monitor up right and again try vesa drivers, vesa is a generic driver which works in most cases.

so try that command again and try to reconfigure Xorg?

---

### Post by Dr. Nick on 2006-10-25
> **maddbaron said:**
> so try that command again and try to reconfigure Xorg?

yeah, I would. you shouldnt be able to harm any files by doing so. It will only modify /etc/X11/xorg.conf and thier are usually backups of it done on any changes.

---

### Post by maddbaron on 2006-10-25
> **Dr. Nick said:**
> yeah, I would. you shouldnt be able to harm any files by doing so. It will only modify /etc/X11/xorg.conf and thier are usually backups of it done on any changes.

i am fiddling around with it via windows made the conf file a .txt and here is my xorg file output

> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"altwin:meta_win"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"vesa"
	Driver		"vesa"
	BusID		"ISA:1"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"vesa"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


can i change anything here then make it an .conf file again and fix the problem that way?

is there also a way to fix the gamma via this method?

---

### Post by Dr. Nick on 2006-10-25
never really played with gamma, my laptop toasted so now i use my desktop all the time, just adjust gamma on the monitor itself.

I did however spot a few potential errors in your xorg, your bus Id looks wrong under the device setting, not sure what it should be set to though. If your video card is on the isa bus it may be right, but most of the times ive seen it on the pci bus.

you should be able to make it a conf and edit it, but if you dont find the error in it, you may just need to redo the configure using the aboce method of dpkg

---

### Post by .t. on 2006-10-25
Indeed, are you really running an ISA card?

---

### Post by maddbaron on 2006-10-25
> **.t. said:**
> Indeed, are you really running an ISA card?


I called aCer and they told me my video card is an Integrated SiS Mirage on an aeus motherboard.

I also see an older version of my output as well would it be helpful if I posted that?

so when I reconfigure dont make it an Isa make it an PCI ? would it help if I editted it manually in windows then renamed it .conf?
 or do i have to do the reconfig process?

---

### Post by maddbaron on 2006-10-25
well this is what I am trying...I just copied a conf file i found in the x11 directory from 7/12/06 and deleted all the conf files from the last few days. I am hoping this reverts it to what it was before I messed it up...I found several errors the mouse, the input device and the isa thing are all wrong on the old file they are all right i think...so here's hoping.

---

### Post by maddbaron on 2006-10-25
IT WORKED!!!!!!!!!! whooooooooo! thanks for keying me into the errors I looked over them and the old file and just copied, and renamed the file a few times and deleted the files from past few days...and it worked! whooo hoo thanks!

---

