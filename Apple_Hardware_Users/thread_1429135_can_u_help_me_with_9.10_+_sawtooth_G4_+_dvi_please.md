---
title: "can u help me with 9.10 + sawtooth G4 + dvi please"
date: 2010-03-13
forum: Apple Hardware Users
---

### Post by surfmonkee on 2010-03-13
so, i have a classic sawtooth G4 350mhz 512 memory 10gb 80gb 'd'drive)

now connected to a Q17+ monitor over vga.

the Q17+ has a dvi input, i have the cable, the G4 has the socket.

Earlier I tried this dvi connection to a clean install of 9.10 over vga but it trashed up and I have started again.

I have only been able to find the rez of the Q17 and not the frequencies and refresh information.

[http://www.tomshardware.com/reviews/good,929-23.html](http://www.tomshardware.com/reviews/good,929-23.html)

how would you suggest I use the dvi out of the G4 or am I just as able to get decent images over vga.

On the install I had working I only managed to get up to a rez of 1080  by editing the X11/etc/confg file

which still makes google look huge, so i figure dvi will let me go up to 1280 

..... will vga go to 1280?

we shall see..................

---

### Post by linuxopjemac on 2010-03-14
can you post your Xorg.conf file please ?

---

### Post by surfmonkee on 2010-03-14
from the terminal i typed exactly 

gedit /etc/X11/xorg.conf


the document that opened is blank.

when i had the pavilion monitor connected i was able to use a template from someone else here at the forum and typed in the specs for frequency and resolution using 

sudo gedit /etc/X11/xorg.conf

I haven't been able to find the specs for my Q17 yet.

hope this helps

---

### Post by linuxopjemac on 2010-03-14
According to everymac you should have a G4/450 DVI aka Sawtooth with an ATI Rage 128 Pro video card.

I would start with the VGA input, I think that's easier. According to this post:
[http://www.gladeindia.com/electronics/html/monitor/html/q17plusspecs.html](http://www.gladeindia.com/electronics/html/monitor/html/q17plusspecs.html)

You have the following recommended:
 	1280 x 1024 @ 60Hz

So we will try to focus on that.
The refresh rates are
horiz: 31-80
vert: 56-75

I will try to make an Xorg.conf file for you. Before we continue, we make sure you have the ATI drivers:
```

sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-r128
```

Just go to /etc/X11 and 

```
sudo nano xorg.conf
```

and paste the following:

```
Section "Monitor"
	Identifier	"Q17"
	Option		"DPMS"
	HorizSync	31-80
	VertRefresh	56-75
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Rage 128 Pro"
	BusID		"PCI:0:16:0"
	Driver		"ati"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies Inc Rage 128 Pro"
	Monitor		"Q17"
	DefaultDepth    24
	SubSection "Display"
		Depth   24
		Modes   "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection
```

Then CTRL-X and "y" to save in the editor. Then see if you have X.
```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

It is barks, then give me the output of /var/log/Xorg.0.log:

```
cat /var/log/Xorg.0.log
```

---

### Post by surfmonkee on 2010-03-14
I am most grateful for your time and effort in helping me. thankyou very much

this information looks awesome and i will follow your instructions later today, right now its time to cook lunch for an ageing mother, its mothers day in the uk today.

thanks again and I will let you know how i go later this evening hopefully...

and thankyou too for finding that information at glade, about my monitor

---

### Post by linuxopjemac on 2010-03-14
It's no problem, it's a hobby of mine to help people like you.

---

### Post by surfmonkee on 2010-03-14
i have done as suggested but maybe i messed up something.

got to the point:

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

the machine went to reboot and it has stuck

screen reads:

starting pbbuttonsb
starting innit crypto discs
hda4 crypt running
starting mouse emulation
cryptswap starting
speech dispatcher configured
starting common unix printing system
pulse audio configured
enabling additional executable binary formats binfmt-support

and a flashing white cursor after the last line


i have hit reset and it begins to log in, i enter the crypto password
and it came back to desktop to log in user and it came back to normal but no option to change the resolution in the display options of the system

i will get you the read of /var/log/Xorg.0.log: in a moment

---

### Post by surfmonkee on 2010-03-14
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[14] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(II) resource ranges after probing:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[17] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] 0	0	0xf00003b0 - 0xf00003bb (0xc) IS[B]
	[22] 0	0	0xf00003c0 - 0xf00003df (0x20) IS[B]
(II) R128(0): PCI bus 0 card 16 func 0
(II) R128(0): Creating default Display subsection in Screen section
	"Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) R128(0): Default visual is TrueColor
(II) R128(0): VGAAccess option set to FALSE, VGA module load skipped
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(**) R128(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Reloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) R128(0): Chipset: "ATI Rage 128 Pro GL PF (AGP)" (ChipID = 0x5046)
(--) R128(0): Linear framebuffer at 0x94000000
(--) R128(0): MMIO registers at 0x90000000
(--) R128(0): VideoRAM: 16384 kByte (64-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(WW) R128(0): Failed to read PCI ROM!
(WW) R128(0): Video BIOS not found!
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
	Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=35 min=12500 max=25000; xclk=14038
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(EE) R128(0): No DFP detected
(II) R128(0): <default monitor>: Using default hsync range of 31.50-37.90 kHz
(II) R128(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
(WW) R128(0): Unable to estimate virtual size
(II) R128(0): Clock range:  12.50 to 250.00 MHz
(II) R128(0): Not using default mode "640x350" (vrefresh out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "320x175" (unknown reason)
(II) R128(0): Not using default mode "640x400" (vrefresh out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "320x200" (unknown reason)
(II) R128(0): Not using default mode "720x400" (vrefresh out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "360x200" (unknown reason)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "320x240" (unknown reason)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "320x240" (unknown reason)
(II) R128(0): Not using default mode "640x480" (vrefresh out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "320x240" (unknown reason)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "320x240" (unknown reason)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "400x300" (unknown reason)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "400x300" (unknown reason)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "400x300" (unknown reason)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "400x300" (unknown reason)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "400x300" (unknown reason)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "1024x768" (unknown reason)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "512x384" (unknown reason)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "512x384" (unknown reason)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "512x384" (unknown reason)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "512x384" (unknown reason)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "512x384" (unknown reason)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "576x432" (unknown reason)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "640x480" (unknown reason)
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "640x480" (unknown reason)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "640x512" (unknown reason)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "640x512" (unknown reason)
(II) R128(0): Not using default mode "1280x1024" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "640x512" (unknown reason)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "800x600" (unknown reason)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "800x600" (unknown reason)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "800x600" (unknown reason)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "800x600" (unknown reason)
(II) R128(0): Not using default mode "1600x1200" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "800x600" (unknown reason)
(II) R128(0): Not using default mode "1792x1344" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "896x672" (unknown reason)
(II) R128(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "896x672" (unknown reason)
(II) R128(0): Not using default mode "1856x1392" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "928x696" (unknown reason)
(II) R128(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "928x696" (unknown reason)
(II) R128(0): Not using default mode "1920x1440" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "960x720" (unknown reason)
(II) R128(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "960x720" (unknown reason)
(II) R128(0): Not using default mode "832x624" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "416x312" (unknown reason)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "576x432" (unknown reason)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "576x432" (unknown reason)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "576x432" (unknown reason)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "576x432" (unknown reason)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "576x432" (unknown reason)
(II) R128(0): Not using default mode "1152x864" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "576x432" (unknown reason)
(II) R128(0): Not using default mode "1360x768" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "680x384" (unknown reason)
(II) R128(0): Not using default mode "1360x768" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "680x384" (unknown reason)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "700x525" (unknown reason)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "700x525" (unknown reason)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "700x525" (unknown reason)
(II) R128(0): Not using default mode "1400x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "700x525" (unknown reason)
(II) R128(0): Not using default mode "1440x900" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "720x450" (unknown reason)
(II) R128(0): Not using default mode "1600x1024" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "800x512" (unknown reason)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "840x525" (unknown reason)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "840x525" (unknown reason)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "840x525" (unknown reason)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "840x525" (unknown reason)
(II) R128(0): Not using default mode "1680x1050" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "840x525" (unknown reason)
(II) R128(0): Not using default mode "1920x1080" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "960x540" (unknown reason)
(II) R128(0): Not using default mode "1920x1200" (hsync out of range)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "960x600" (unknown reason)
(II) R128(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "960x720" (unknown reason)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "1024x768" (unknown reason)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "1024x768" (unknown reason)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(EE) R128(0): FBIOPUT_VSCREENINFO: Invalid argument
(II) R128(0): Not using default mode "1024x768" (unknown reason)
(--) R128(0): Virtual size is 800x600 (pitch 800)
(**) R128(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) R128(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) R128(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) R128(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) R128(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	2	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	2	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	2	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	2	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	1	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	1	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	1	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	1	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	2	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	2	0x00000000 - 0x00000000 (0x1) IX[B]
	[17] -1	1	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	1	0x00000000 - 0x00000000 (0x1) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[21] 0	0	0xf00003b0 - 0xf00003bb (0xc) IS[B]
	[22] 0	0	0xf00003c0 - 0xf00003df (0x20) IS[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:00:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:10.0
(II) [drm] loaded kernel module for "r128" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) R128(0): [drm] Using the DRM lock SAREA also for drawables.
(II) R128(0): [drm] framebuffer handle = 0x94000000
(II) R128(0): [drm] added 1 reserved context for kernel
(II) R128(0): X context handle = 0x1
(II) R128(0): [drm] installed DRM signal handler
(II) R128(0): [agp] Mode 0x07000201 [AGP 0x106b/0x0020; Card 0x1002/0x5046]
(II) R128(0): [agp] 8192 kB allocated with handle 0x00000001
(II) R128(0): [agp] ring handle = 0x00000000
(II) R128(0): [agp] Ring mapped at 0x49054000
(II) R128(0): [agp] ring read ptr handle = 0x00101000
(II) R128(0): [agp] Ring read ptr mapped at 0x48025000
(II) R128(0): [agp] vertex/indirect buffers handle = 0x00102000
(II) R128(0): [agp] Vertex/indirect buffers mapped at 0x49155000
(II) R128(0): [agp] AGP texture map handle = 0x00302000
(II) R128(0): [agp] AGP Texture map mapped at 0x49355000
(II) R128(0): [drm] register handle = 0x90000000
(II) R128(0): [dri] Visual configs initialized
(II) R128(0): CCE in BM mode
(II) R128(0): Using 8 MB AGP aperture
(II) R128(0): Using 1 MB for the ring buffer
(II) R128(0): Using 2 MB for vertex/indirect buffers
(II) R128(0): Using 5 MB for AGP textures
(II) R128(0): Memory manager initialized to (0,0) (800,2457)
(II) R128(0): Reserved area from (0,600) to (800,602)
(II) R128(0): Largest offscreen area available: 800 x 1855
(II) R128(0): Reserved back buffer from (0,602) to (800,1202)
(II) R128(0): Reserved depth buffer from (0,1202) to (800,1803)
(II) R128(0): Reserved depth span from (0,1802) offset 0x57fd00
(II) R128(0): Reserved 8704 kb for textures at offset 0x77f880
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		30 128x128 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 7212)
(II) R128(0): Largest offscreen area available: 800 x 651
(II) R128(0): DPMS enabled
(II) R128(0): [DRI] installation complete
(II) R128(0): [drm] Added 128 16384 byte vertex/indirect buffers
(II) R128(0): [drm] Mapped 128 vertex/indirect buffers
(II) R128(0): [drm] dma control initialized, using IRQ 48
(II) R128(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:10.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:10.0
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: Loaded and initialized /usr/lib/dri/r128_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device Mouseemu virtual keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Mouseemu virtual keyboard: always reports core events
(**) Mouseemu virtual keyboard: Device: "/dev/input/event5"
(II) Mouseemu virtual keyboard: Found keys
(II) Mouseemu virtual keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Mouseemu virtual keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device PMU
(**) PMU: always reports core events
(**) PMU: Device: "/dev/input/event1"
(II) PMU: Found keys
(II) PMU: Configuring as keyboard
(II) XINPUT: Adding extended input device "PMU" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Mouseemu virtual mouse
(**) Mouseemu virtual mouse: always reports core events
(**) Mouseemu virtual mouse: Device: "/dev/input/event6"
(II) Mouseemu virtual mouse: Found 14 mouse buttons
(II) Mouseemu virtual mouse: Found x and y relative axes
(II) Mouseemu virtual mouse: Found scroll wheel(s)
(II) Mouseemu virtual mouse: Configuring as mouse
(**) Mouseemu virtual mouse: YAxisMapping: buttons 4 and 5
(**) Mouseemu virtual mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Mouseemu virtual mouse" (type: MOUSE)
(**) Mouseemu virtual mouse: (accel) keeping acceleration scheme 1
(**) Mouseemu virtual mouse: (accel) filter chain progression: 2.00
(**) Mouseemu virtual mouse: (accel) filter stage 0: 20.00 ms
(**) Mouseemu virtual mouse: (accel) set acceleration profile 0
(II) Mouseemu virtual mouse: initialized for relative axes.
(II) config/hal: Adding input device Alps Electric Apple USB Keyboard
(**) Alps Electric Apple USB Keyboard: always reports core events
(**) Alps Electric Apple USB Keyboard: Device: "/dev/input/event2"
(II) Alps Electric Apple USB Keyboard: Found keys
(II) Alps Electric Apple USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Alps Electric Apple USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech M4848
(**) Logitech M4848: always reports core events
(**) Logitech M4848: Device: "/dev/input/event3"
(II) Logitech M4848: Found 1 mouse buttons
(II) Logitech M4848: Found x and y relative axes
(II) Logitech M4848: Configuring as mouse
(**) Logitech M4848: YAxisMapping: buttons 4 and 5
(**) Logitech M4848: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech M4848" (type: MOUSE)
(**) Logitech M4848: (accel) keeping acceleration scheme 1
(**) Logitech M4848: (accel) filter chain progression: 2.00
(**) Logitech M4848: (accel) filter stage 0: 20.00 ms
(**) Logitech M4848: (accel) set acceleration profile 0
(II) Logitech M4848: initialized for relative axes.

---

### Post by linuxopjemac on 2010-03-14
Maybe you have to find the right modelines and add them to your Xorg.conf file. Have a look [here]("http://mac.linux.be/content/setting-xorgconf-manually-xrandr") and give me the modelines of your system at your preferred resolution.

---

### Post by surfmonkee on 2010-03-14
modelines..... mmmm that sounds like a bit of googling and searching, which is no bad thing.

I have one other idea up my sleeve which I may try in the week. sunday night is upon is as is the working week ahead..... it pays the bills...
so for a moment, mrs ubuntu has to take a back seat.

I'll be back...... along with a new thread about problems trying to install either avidemux or the ken video editor, neither will install, but thats for another day....

thanks for your time today, its much appreciated.

---

### Post by linuxopjemac on 2010-03-15
Tell me what happens if you boot your system. Does your system (try to) go into a graphical user interface or does it end up in a text environment ?

---

### Post by surfmonkee on 2010-03-15
it boots up normally, first screen i type in my encrpyted disc password, then i sign in the user and the regular desktop appears and works fine, its just stuck in 800/600

In almost every other espect it is just fine, i did try to install avidemux but it wouldnt let me due so 'some dependencies' but i can live with out that for now

the machine runs just like i would expect it to......other than a little sluggush which is probably due to a 350mhgz processor and 512 ram....

---

### Post by linuxopjemac on 2010-03-15
ok, you have a gui, that's something, we need to get more than 800x600 out of that machine. I am sure if you follow the link I gave you, that you will be able to get a higher resolution.

---

### Post by linuxopjemac on 2010-03-15
avedimux is in the repositories, I don't know about PPC...

```
sudo apt-get install avidemux
```

---

### Post by surfmonkee on 2010-03-15
i have looked at the link you suggested 
xrandr provides me this information but i have no clue what to do with it or how to add modes or what modes i need.

i checked to see if the ati driver is instaled by trying the download again and it said i was already up to date, yet if i go to system/admin/drivers it comes up emtpy, should i see anything in drivers?


its horrible being stuck at 600/800 and i have googled till i am blue in the face.

xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0

---

### Post by linuxopjemac on 2010-03-15
I can't help you more than this. You have to follow the link and find the modelines and add them as was done in the thread. Sorry.

---

### Post by surfmonkee on 2010-03-15
thanks for trying to help

as an experienced computer user i can manage most things, ubuntu is new to me and mode lines are a complete mystery so i shall stay in 800/600 till i get fed up with it and go back to os x

perhaps one day ubuntu will recognise graphics and then i will make the change to it.

thanks anyway.

---

### Post by linuxopjemac on 2010-03-15
I don't think that's going to happen as you have an outdated architecture where not a lot of progress is being made anymore. Installers for ppc don't make an Xorg.conf file for you, that's the problem.

---

### Post by surfmonkee on 2010-03-15
> **linuxopjemac said:**
> Installers for ppc don't make an Xorg.conf file for you, that's the problem.

so they dont make an xorg for ppc yet they make a version of ubuntu for ppc... ok that makes sense i guess

i for one, can not be only person to do this on a G4

it cant be that hard to get an OS to produce 1280 resolution and altho my graphics may be a bit dated, it should be so difficult to get a decent resolution 'out of the box' especially as ubuntu does so many other great things 'out of the box'

the avidemux program i wanted was in the software center but neither of the two versions would install due to some dependencies missing, again, i would have thought that would be solved if it is a clean install.

oh well, i will come back to ubuntu another day with another computer and my G4 will go back to OS X later today so i can work in a decent resolution

thanks for your time.

ubuntu is not for me after all................

---

### Post by linuxopjemac on 2010-03-16
Maybe you can try Debian Lenny. It looks less impressive but it works a lot better to my opinion on PPC Apples.

If you have a wired internet connection you might want to try a netinstall:

[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso)

This is what I used on my PowerBook G3 Pismo.

---

### Post by surfmonkee on 2010-03-16
i had debian on a net install running perfectly right before i went for 9.10

i really want 9.10 because imo it looks alot better ,i like its built in torrent client, which i really want to replace utorrent on windows.

i havent really had time to compare the two but debian only gave me 800/600 initally.

i have done a lot of googling on modelines now but still feel that its too much messing about so i am hestitant to put debian back on the ppc.

os x went back on last night and at least i can get on with my work now.

id be ALOT happier if i know this modeline thing wont happen with my two XP machines, thats where i really want 9.10.... i need to GET RID OF WINDOWS!

the ppc try was exactly that, a try out, and sadly its left me feeling like i cant be bothered with linux JUST YET.

---

