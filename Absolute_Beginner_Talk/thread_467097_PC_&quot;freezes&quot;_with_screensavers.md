---
title: "PC &quot;freezes&quot; with screensavers"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by JimPletcher on 2007-06-07
With 7.04

The PC will lock up (no mouse or keyboard control) when selecting ceratin screensavers.

Also, when running several (I haven't tried them all) screensavers the PC locks and the only way to reboot is by removing AC power (or equivalent).

I could care less about screen savers, but is this an indication that something more serious is wrong?

---

### Post by whizbaby on 2007-06-07
Please post the contents of your

/etc/X11/xorg.conf

dont have enough info to say anything...

---

### Post by muguwmp67 on 2007-06-07
Are the screensavers you are having trouble with prefixed by GL?  Although I don't think this should cause your pc to crash, its possible that you don't have the right graphics driver installed.  What happens when you run a simple screensaver like laser or lightning?

Still post your xorg.conf though.

---

### Post by w4ett on 2007-06-07
Also post the result of  glxinfo  I suspect you do not have direct rendering enabled.  I had the same problem at one time.

---

### Post by JimPletcher on 2007-06-07
here is the conf file


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
	Load	"i2c"
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
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LCD52V"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Monitor		"LCD52V"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by JimPletcher on 2007-06-07
here's the glxinfo:   GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x46 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
pletcher@Ubuntu:~$

---

### Post by whizbaby on 2007-06-07
1st thing you can try is commenting out (in Monitor Section)

Option           "DPMS"

which can cause problems with screensavers (you do that by putting a # in front of the line then save and restart the xserver)

2nd type
glxinfo -v| grep direct
 
it will say

direct rendering: yes

(or direct rendering: no)

is direct rendring enabled?

---

### Post by w4ett on 2007-06-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/49782](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/49782) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I see that DRI is loading in your upload. does GLXGEARS run slowly or lockup?    Apparently there is a bug in the way the Xorg Via driver implements Direct Rendering.  This will make the 3D intensive apps (screensavers, Google Earth, etc..) lock up, or at the least run V.....E....R.....Y slowly.
Aside from the bug being fixed or new drivers released, I would recommend disabling the screensavers and consider installing a new graphics card (preferably Nvidia--fewer driver issues)

---

### Post by JimPletcher on 2007-06-07
Response to  muguwmp67,

The problem is not only with GL prefixed screensavers, it seems to be with MOST of them.
Just touching AntSpotlight kills the PC immediately, but some of the others can runfor a while before the freeze.

---

### Post by whizbaby on 2007-06-07
I corrected a few typos in my post, if you write from a mailprogram you'll have to reread it.

---

### Post by muguwmp67 on 2007-06-07
It sounds like you are having a problem with 3d rendering and the via chipset drivers.  Does the PC lock up if you change the mode to 'Blank Screen Only'?  Do they lock up in the preview window?

---

### Post by JimPletcher on 2007-06-07
direct renrering IS enabled.

I just commented out DPMS in the monitor section and rebooted

Just froze again.

ADDING a video card to this small form factor PC is not an option

---

### Post by JimPletcher on 2007-06-07
Blank Screen does NOT cause a lockup.

I can easily NOT use scrensavers, but am concerned about other ramifications.

If absolutely neccessary, I can relegate this PC to SSL server use only without screensavers.
I use SSL server to access my LAN from where I  can Remote Desktop to client's servers via VPN.
3D rendering wouldn't/shouldn't bother that.


Thanks for the help guys!!!!

---

### Post by w4ett on 2007-06-07
It seems that there are a number of bugs with the S3  Via open source driver....Please see:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+bug/43154)

all the posts there relate the same problems you have.  Sorry to not be of more help.

Further, I bought a low profile ATI card (9200SE 64MB)  a few weeks ago on ebay for $14 inc shipping  that might work for your system....ATI 9200 does have driver issues, but it's a cheap fix even considering a few bugs that need attention.   [http://stores.ebay.com/ReTekDirect](http://stores.ebay.com/ReTekDirect)

---

