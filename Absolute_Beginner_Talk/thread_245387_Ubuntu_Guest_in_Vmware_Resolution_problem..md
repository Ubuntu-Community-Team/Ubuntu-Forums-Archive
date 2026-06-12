---
title: "Ubuntu Guest in Vmware Resolution problem."
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by wondergod on 2006-08-27
Ok lets begin I am running ubuntu under vmware just to test it out before I decide if I wanna dual boot it. Now keep in mind I'm a newbie and I have searched google, and the forums but am at a lost...OK so back to what I was saying...Windows is the host..Ubuntu is the guest in vmware and I have a 19" widescreen hanns-g monitor and I can't get 1400x900 running in it. My montior is capable of 1400x900 at 75Mhz however I don't mind running it at 60Mhz. Ok so far this is what I have done...

I've edited my ubuntu.vmx with the

> svga.maxWidth = "1400"
svga.maxHeight = "900" 

Installed vmware tools and ran vmware-config-tools.pl..however I was never prompted anything about resolution. Also ran vmware toolbox and nothing in there has anything to do with video.

Went in my /etc/X11/xorg.conf and this is what it has(I added the 1400x900)

```
Section "Device"
	Identifier	"VMWare Inc [VMware SVGA II] PCI Display Adapter"
	Driver		"vmware"
	BusID		"PCI:0:15:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VMWare Inc [VMware SVGA II] PCI Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Now checking my xorg.0.log I see this

```
(II) VMWARE: driver for VMware SVGA: vmware0405, vmware0710
(II) Primary Device is: PCI 00:0f:0
(--) Chipset vmware0405 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] 0	0	0x000b8000 - 0x000bffff (0x8000) MX[B]
	[1] 0	0	0x000b0000 - 0x000b7fff (0x8000) MX[B]
	[2] 0	0	0x000a0000 - 0x000affff (0x10000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xec000000 - 0xec7fffff (0x800000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] 0	0	0x200103c0 - 0x200103df (0x20) IX[B]
	[12] 0	0	0x200103b0 - 0x200103bb (0xc) IX[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001480 - 0x000014bf (0x40) IX[B]
	[16] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[17] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[18] -1	0	0x00001060 - 0x0000107f (0x20) IX[B]
	[19] -1	0	0x00001050 - 0x0000105f (0x10) IX[B]
	[20] -1	0	0x000014c0 - 0x000014cf (0x10) IX[B](B)
(II) resource ranges after probing:
	[0] 0	0	0x000b8000 - 0x000bffff (0x8000) MX[B]
	[1] 0	0	0x000b0000 - 0x000b7fff (0x8000) MX[B]
	[2] 0	0	0x000a0000 - 0x000affff (0x10000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xec000000 - 0xec7fffff (0x800000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] 0	0	0x200103c0 - 0x200103df (0x20) IX[B]
	[12] 0	0	0x200103b0 - 0x200103bb (0xc) IX[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001480 - 0x000014bf (0x40) IX[B]
	[16] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[17] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[18] -1	0	0x00001060 - 0x0000107f (0x20) IX[B]
	[19] -1	0	0x00001050 - 0x0000105f (0x10) IX[B]
	[20] -1	0	0x000014c0 - 0x000014cf (0x10) IX[B](B)
(II) Setting vga for screen 0.
(--) VMWARE(0): VMware SVGA regs at (0x14c0, 0x14c1)
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(--) VMWARE(0): caps:  0x000083E2
(--) VMWARE(0): depth: 24
(--) VMWARE(0): bpp:   32
(--) VMWARE(0): vram:  16777216
(--) VMWARE(0): pbase: 0xf0000000
(--) VMWARE(0): mwidt: 1400
(--) VMWARE(0): mheig: 900
(--) VMWARE(0): depth: 24
(--) VMWARE(0): bpp:   32
(--) VMWARE(0): w.red: 8
(--) VMWARE(0): w.grn: 8
(--) VMWARE(0): w.blu: 8
(--) VMWARE(0): vis:   4
(**) VMWARE(0): Depth 24, (--) framebuffer bpp 32
(==) VMWARE(0): RGB weight 888
(==) VMWARE(0): Default visual is TrueColor
(==) VMWARE(0): Using HW cursor
(==) VMWARE(0): Using gamma correction (1.0, 1.0, 1.0)
(II) VMWARE(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) VMWARE(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) VMWARE(0): Clock range:   0.00 to 400000.00 MHz
(II) VMWARE(0): Not using default mode "640x350" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "640x400" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "720x400" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "640x480" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "640x480" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "640x480" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "800x600" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "800x600" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "800x600" (hsync out of range)
(II) VMWARE(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1024x768" (hsync out of range)
(II) VMWARE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1024x768" (hsync out of range)
(II) VMWARE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1024x768" (hsync out of range)
(II) VMWARE(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1152x864" (hsync out of range)
(II) VMWARE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1280x960" (hsync out of range)
(II) VMWARE(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1280x960" (hsync out of range)
(II) VMWARE(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1280x1024" (hsync out of range)
(II) VMWARE(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1280x1024" (hsync out of range)
(II) VMWARE(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1280x1024" (hsync out of range)
(II) VMWARE(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1792x1344" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1792x1344" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1856x1392" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1856x1392" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "832x624" (vrefresh out of range)
(II) VMWARE(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1152x864" (hsync out of range)
(II) VMWARE(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1400x1050" (hsync out of range)
(II) VMWARE(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1400x1050" (hsync out of range)
(II) VMWARE(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1400x1050" (hsync out of range)
(II) VMWARE(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1400x1050" (hsync out of range)
(II) VMWARE(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1440x900" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1600x1024" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1680x1050" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1680x1050" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1680x1050" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1920x1200" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1920x1200" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) VMWARE(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) VMWARE(0): Not using mode "1400x900" (no mode of this name)
(II) VMWARE(0): Not using default mode "1280x800" (width too large for virtual size)
(II) VMWARE(0): Not using default mode "1280x768" (width too large for virtual size)
(II) VMWARE(0): Not using default mode "1152x768" (width too large for virtual size)
(--) VMWARE(0): Virtual size is 1024x768 (pitch 1024)
(**) VMWARE(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) VMWARE(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) VMWARE(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) VMWARE(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) VMWARE(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) VMWARE(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) VMWARE(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) VMWARE(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(==) VMWARE(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x000b8000 - 0x000bffff (0x8000) MX[B]
	[1] 0	0	0x000b0000 - 0x000b7fff (0x8000) MX[B]
	[2] 0	0	0x000a0000 - 0x000affff (0x10000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xec800000 - 0xec800fff (0x1000) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xec000000 - 0xec7fffff (0x800000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] 0	0	0x200103c0 - 0x200103df (0x20) IX[B]
	[12] 0	0	0x200103b0 - 0x200103bb (0xc) IX[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001480 - 0x000014bf (0x40) IX[B]
	[16] -1	0	0x00001400 - 0x0000147f (0x80) IX[B]
	[17] -1	0	0x00001080 - 0x000010ff (0x80) IX[B]
	[18] -1	0	0x00001060 - 0x0000107f (0x20) IX[B]
	[19] -1	0	0x00001050 - 0x0000105f (0x10) IX[B]
	[20] -1	0	0x000014c0 - 0x000014cf (0x10) IX[B](B)
(II) VMWARE(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) VMWARE(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
```


Now I realize I probably have to write up a modeline for my monitor however I have read many sites about making one but I'm afraid I screw up my monitor with a incorrect one. Could someone please help or point me in the right direction on a howto or whatever....Thanks.

---

### Post by Kilz on 2006-08-27
The problem is that when you are running vmware you are using a virtual graphics card. Not the one you have installed on your computer but a svga that isnt capable of the higher resolutions. 
```
Section "Device"
	Identifier	"VMWare Inc [[COLOR="Red"]VMware SVGA II[/COLOR]] PCI Display Adapter"
	Driver		"vmware"
	BusID		"PCI:0:15:0"
EndSection
```

Once installed to your hard drive Ubuntu will use the graphics card installed. It may need to have the drivers installed, but should be capable of the resolution your hardware is capable of.

---

### Post by wondergod on 2006-08-27
Thanks I guess I'll dual boot it...just to see what its like at fll resolution...

---

