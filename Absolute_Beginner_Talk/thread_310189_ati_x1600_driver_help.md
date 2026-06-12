---
title: "ati x1600 driver help"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by sindrum_murdnis on 2006-11-30
Can someone please lead me in the right direction or tell me how to install drivers for my ATI x1600 GPU. I'm tearing my hair out trying to do this, every time I install drivers from the ATI site my computer freezes at boot. ](*,) 

My specs are 

AMD 64 +3000
ATI x1600 pro
2 hard drives one windows one ubuntu 6.10
1.00 gig memory

---

### Post by psp_gamer on 2006-11-30
I'm in the same boat... is yours agp also?

---

### Post by redDEADresolve on 2006-11-30
I have an ati x1600 and have everything working 100%. I use this guides from the unofficial ATI Linux Installation wiki & they work.

If you are using Dapper Drake 6.06:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

If you are using Edgy Eft 6.10:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by sindrum_murdnis on 2006-11-30
Yes sir, agp is correct. its funny cause i read a way that worked for me but i cant find the forum again. im in the process of trying a few more things. its going slow cause i mess it up and have to reinstall it again but if i find anything ill post.

---

### Post by sindrum_murdnis on 2006-11-30
thanks for the post i did what was on the site and it worked. theres something else now. say i open anything and move the window or scroll everything gets all jumbled together unitl i minimize or maximize the screen. any ideas on what this might be.

---

### Post by sindrum_murdnis on 2006-11-30
i attached a few pics of my desktop.these windows were stationary not moving. its like i move them then they get all screwy. any ideas?

---

### Post by redDEADresolve on 2006-11-30
I checked your pics I don't know what could be wrong. I only have two suggestions:

did you undo any changes from the previous install?

are you using beryl or compiz? Sometimes you need to tweak XGL with an X1600 card in edgy.

Anyone else more knowledgeable able to HELP?

---

### Post by sindrum_murdnis on 2006-11-30
this was a fresh install and the only things i had done up till this point was install updates and installed the ati drivers. No i did not install beryl or compiz.

---

### Post by redDEADresolve on 2006-11-30
I'm sorry I'm not more help try the irc room. I've had great luck there.

---

### Post by sindrum_murdnis on 2006-12-01
ok heres the solution to my problem. 

```

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg

```
Select ATI drivers and leave everything else as is. After that just reboot...

I wasn't able to log back in after i had done this so i rebooted again and selected recover console at the boot menu and entered this.

```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg

```
Select fglrx drivers leaving everything else the way they are. 

Reboot
thats about it it seems to be working fine now. I found this info searching google and sent me to a ubuntu forum entry. :) hope this helps somebody else out.

---

### Post by Zober on 2007-01-02
Hello,
I followed the guide above and still no luck.

glxgears --print fps maxes out at 146 fps.

**My Specs:**
[INDENT]Ubuntu Edgy 6.10
AMD 3200+
ATI x1600 Pro 512MB AGP
1.5 GB RAM
2x 160GB Drives
[/INDENT]

**GLXINFO Report:**
[INDENT]kit@WGBlackBox:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x3c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None[/INDENT]

**My xorg.conf file:**
[INDENT]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Generic Video Card (Ati Custom"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	VideoRam	524288
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card (Ati Custom"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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
EndSection[/INDENT]

---

### Post by Zober on 2007-01-02
**Finally my Xorg.0.log**

[INDENT]X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux WGBlackBox 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan  2 15:47:33 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card (Ati Custom"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3188 card 1043,80a3 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:08:0: chip 105a,3373 card 1043,80f5 rev 02 class 01,04,00 hdr 00
(II) PCI: 00:0a:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 00:0d:0: chip 1102,0008 card 1102,1021 rev 00 class 04,01,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,80b0 rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1002,71c2 card 1002,030b rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71e2 card 1002,030a rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfcf00000 - 0xfd4fffff (0x600000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd4800000 - 0xf4dfffff (0x20600000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV530 [Radeon X1600] rev 0, Mem @ 0xe0000000/28, 0xfd400000/16, I/O @ 0xa000/8, BIOS @ 0xfd300000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV530 [Radeon X1600] (Secondary) rev 0, Mem @ 0xfd000000/16
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfda00000 - 0xfda000ff (0x100) MX[B]
	[1] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[2] -1	0	0xfde00000 - 0xfde1ffff (0x20000) MX[B]
	[3] -1	0	0xfdf00000 - 0xfdf00fff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xfd000000 - 0xfd00ffff (0x10000) MX[B](B)
	[6] -1	0	0xfd300000 - 0xfd31ffff (0x20000) MX[B](B)
	[7] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[12] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfda00000 - 0xfda000ff (0x100) MX[B]
	[1] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[2] -1	0	0xfde00000 - 0xfde1ffff (0x20000) MX[B]
	[3] -1	0	0xfdf00000 - 0xfdf00fff (0x1000) MX[B]
	[4] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[5] -1	0	0xfd000000 - 0xfd00ffff (0x10000) MX[B](B)
	[6] -1	0	0xfd300000 - 0xfd31ffff (0x20000) MX[B](B)
	[7] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[12] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[19] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[27] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfda00000 - 0xfda000ff (0x100) MX[B]
	[5] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[6] -1	0	0xfde00000 - 0xfde1ffff (0x20000) MX[B]
	[7] -1	0	0xfdf00000 - 0xfdf00fff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xfd000000 - 0xfd00ffff (0x10000) MX[B](B)
	[10] -1	0	0xfd300000 - 0xfd31ffff (0x20000) MX[B](B)
	[11] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.28.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9250/9200 Series (RV280 5961),
	RADEON 9250/9200 Series (RV280 5962),
	RADEON 9250/9200 Series (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 GTO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
	RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
	RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
	RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
	MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
	MOBILITY RADEON X700 XL (M26-XC 564F),
	RADEON 9000/9100 IGP Series (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000 IGP (RL300MB 7835),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
	RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
	RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1600 Series (RV515 7140), RADEON X1300 Series (RV515 7142),
	MOBILITY FireGL (M54 GL 7144), MOBILITY RADEON X1400 (M54 7145),
	RADEON X1300 Series (RV515 7146), MOBILITY RADEON X1300 (M52 7149),
	MOBILITY RADEON X1300 (M52 714A), RADEON X1300 Series (RV515 714D),
	RADEON X1300 Series (RV515 714E), FireGL V3300 (RV515 7152),
	RADEON X1300 Series (RV515 715E), RADEON X1300 (RV516 7180),
	RADEON X1600 Series (RV516 7181), RADEON X1300 (RV516 7183),
	MOBILITY RADEON X1450 (M64P 7186), RADEON X1300 (RV516 7187),
	MOBILITY RADEON X1350 (M62P 718B),
	MOBILITY RADEON X1350 (M62CSP 718C),
	MOBILITY RADEON X1450 (M64CSP 718D),
	MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
	RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
	RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
	RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
	RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
	RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
	RADEON X1900 (R580 724D), FireStream 2U (R580 724E),
	FireStream 2U (R580 724F), RADEON X1600 Series (RV530 71C0),
	RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
	MOBILITY RADEON X1600 (M56 71C5),
	RADEON X1600 Series (RV530 LE 71C6),
	RADEON X1600 Series (RV530 VE 71CE), FireGL V3400 (RV530 71D2),
	MOBILITY RADEON X1700 (M66-XT 71D6), FireGL V5200 (RV530 71DA),
	RADEON X1600 Series (RV530 SE 71DE), RADEON X1600 XT (RV535 XT 71C1),
	MOBILITY FireGL V5250 (M66GL 71D4),
	MOBILITY RADEON X1700 (M66-P 71D5), RADEON Xpress 1200 (RS600 7941),
	RADEON Xpress 1200 (RS600 7942)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1                           
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:28:12
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON X1600 Series (RV530 71C2) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfda00000 - 0xfda000ff (0x100) MX[B]
	[5] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[6] -1	0	0xfde00000 - 0xfde1ffff (0x20000) MX[B]
	[7] -1	0	0xfdf00000 - 0xfdf00fff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xfd000000 - 0xfd00ffff (0x10000) MX[B](B)
	[10] -1	0	0xfd300000 - 0xfd31ffff (0x20000) MX[B](B)
	[11] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[25] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e1858
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfda00000 - 0xfda000ff (0x100) MX[B]
	[5] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[6] -1	0	0xfde00000 - 0xfde1ffff (0x20000) MX[B]
	[7] -1	0	0xfdf00000 - 0xfdf00fff (0x1000) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xfd000000 - 0xfd00ffff (0x10000) MX[B](B)
	[10] -1	0	0xfd300000 - 0xfd31ffff (0x20000) MX[B](B)
	[11] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[28] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[30] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[33] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[35] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) fglrx(0): PCI bus 1 card 0 func 0
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
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON X1600 Series (RV530 71C2)" (Chipset = 0x71c2)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x030b)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfd400000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
[/indent]

---

### Post by Zober on 2007-01-02
[INDENT]
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.28.8
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): Video RAM override, using 524288 kB instead of 524288 kB
(**) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 115  Serial#: 1196634425
(II) fglrx(0): Year: 2005  Week: 35
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.634 redY: 0.354   greenX: 0.304 greenY: 0.581
(II) fglrx(0): blueX: 0.143 blueY: 0.102   whiteX: 0.310 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HVEY803980
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay not supported on this hardware
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 51 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 169.2 MHz (scaled from 0.0 MHz), 97.0 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1280x1024"  169.20  1280 1376 1512 1744  1024 1025 1028 1078 +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0):  Default mode "1024x768": 139.1 MHz (scaled from 0.0 MHz), 98.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "1024x768"  139.05  1024 1104 1216 1408  768 769 772 823 +hsync
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"  113.30  1024 1096 1208 1392  768 769 772 814 +hsync
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"  100.18  1024 1088 1200 1376  768 769 772 809 +hsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 83.9 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"   83.94  800 856 944 1088  600 601 604 643 +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"   72.85  640 680 752 864  480 481 484 527 +hsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0):  Default mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907 +hsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 143.5 MHz (scaled from 0.0 MHz), 91.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1152x864"  143.47  1152 1232 1360 1568  864 865 868 915 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
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
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 169.2 MHz (scaled from 0.0 MHz), 97.0 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1280x1024"  169.20  1280 1376 1512 1744  1024 1025 1028 1078 +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0):  Default mode "1024x768": 139.1 MHz (scaled from 0.0 MHz), 98.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "1024x768"  139.05  1024 1104 1216 1408  768 769 772 823 +hsync
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"  113.30  1024 1096 1208 1392  768 769 772 814 +hsync
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"  100.18  1024 1088 1200 1376  768 769 772 809 +hsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 83.9 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"   83.94  800 856 944 1088  600 601 604 643 +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.17  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"   72.85  640 680 752 864  480 481 484 527 +hsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.40  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0):  Default mode "1280x720": 60.5 MHz (scaled from 0.0 MHz), 37.0 kHz, 50.0 Hz
(II) fglrx(0): Modeline "1280x720"   60.46  1280 1328 1456 1632  720 721 724 741 +hsync
(**) fglrx(0):  Default mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907 +hsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 143.5 MHz (scaled from 0.0 MHz), 91.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1152x864"  143.47  1152 1232 1360 1568  864 865 868 915 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
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
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x0000089b
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfda00000 - 0xfda000ff (0x100) MX[B]
	[7] -1	0	0xfdc00000 - 0xfdc03fff (0x4000) MX[B]
	[8] -1	0	0xfde00000 - 0xfde1ffff (0x20000) MX[B]
	[9] -1	0	0xfdf00000 - 0xfdf00fff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[11] -1	0	0xfd000000 - 0xfd00ffff (0x10000) MX[B](B)
	[12] -1	0	0xfd300000 - 0xfd31ffff (0x20000) MX[B](B)
	[13] -1	0	0xfd400000 - 0xfd40ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[22] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b80f (0x10) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[32] -1	0	0x0000c800 - 0x0000c803 (0x4) IX[B]
	[33] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[34] -1	0	0x0000d400 - 0x0000d43f (0x40) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[36] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[37] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[38] -1	0	0x0000e800 - 0x0000e83f (0x40) IX[B]
	[39] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x0f8ff000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x0f8ff000)
(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xe0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
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
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
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
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
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
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
[/INDENT]

Sorry for double post, I wanted to be thorough

---

### Post by mrfuzzemz on 2007-01-04
Anyone having problems with installing the *LATEST* ATI drivers should be sure to blacklist the included ubuntu restricted fglrx.  If you are still having problems you may want to be sure to print out the HOWTO and do everything in recovery mode.  Also be sure to disable compositing if things run slow and you aren't getting direct rendering.

---

### Post by mrfuzzemz on 2007-01-04
Zober: 
    I don't like this here:

> OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


I had this problem for a while myself.  This should be displaying something like this displaying the model of your card:

> 
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6234 (8.32.5)


Are you using ubuntu's included drivers or trying to install ATI's latest?

---

### Post by Zober on 2007-01-11
> **mrfuzzemz said:**
> Zober: 

Are you using ubuntu's included drivers or trying to install ATI's latest?

I think I've tried everything.

I attempted running an auto install of ATI's driver, with the package they have on their site.  I've also compiled distro specific packages using the ATI's official linux driver.  And finally I've also tried using:
apt-get install xorg-driver-fglrx

I also formatted the machine and put SuSE 10.2 on it because their site claimed to have full support for the card, no such luck.

I've been at it for at least 3 weeks now, and I havent seen a single post of anyone getting this to work on the AGP 512MB version of the card.

Any ideas?

---

### Post by dieselpower79 on 2007-01-14
Just to help people who have an ATI x1600 card (PCI Express) and are trying to get Beryl working, Here is the solution I used and it works great!

1. Install Ubuntu Edgy

2. Get latest software updates

3. Download latest ATI driver (approx 55mb)

4. Follow this guide 'Instructions for 6.10 (Edgy)' [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
Follow each section from the top, step by step carefully (don't skip parts if a command doesn't run) 

5. After running **sudo aticonfig --initial** and **sudo aticonfig --overlay-type=Xv** Reboot

6. Ensure driver is installed correctly by typing **fglrxinfo** in a terminal window
You should get this:-

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6286 (8.33.6)

If not, you have not installed the driver correctly, try previous sections again.

7. Type **glxgears** in a terminal window (should get some cogs moving around)
Close the window.

8. Type **fgl_glxgears** in a terminal window (should get some even fancier moving cogs) Close the window after 10 seconds, You should get a report of frames per second etc. This now proves you have 3d support!

9. Enable 'universe' repository by ticking 'Community maintained open source software (universe)' within System | Software Sources

10. Follow this guide [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")
Follow this from the very top down to 'Changing your standard login', I didn't want to change this until I knew it worked.

11. Reboot and log into into your newly created 'xgl' session

12. Run **beryl-manager** in a terminal window. Beryl should launch!

13. If successful add **beryl-manager** to the 'Startup Programs' under System | Preferences | Sessions.

I'm a complete newbie to Linux but was very interested in getting XGL/Beryl working. After trying numerous instructions and screwing up my Ubuntu installs this procedure FINALLY worked. I hope it helps others and prevents further hair loss to the community.........:cool:

---

### Post by Einsam on 2007-01-15
...

---

### Post by mrfuzzemz on 2007-01-16
To anyone that is still having trouble:

Be sure that you are doing all of this in recovery mode if you are installing the latest driver from the ATI site! You don't want an fglrx driver loaded while installing.  You will also want to blacklist the included fglrx.

If you can't get it, just run with the included driver as it is simplest to install.

Post here if you still have questions.

---

### Post by SVFUSiON on 2007-01-16
> **sindrum_murdnis said:**
> i attached a few pics of my desktop.these windows were stationary not moving. its like i move them then they get all screwy. any ideas?

I am having the same problem as this user. I tried his solution but it just locks up on boot when I dpkg-reconfigure xserver-xorg

I tired the ATi and the fglrx drivers. The VESA works but I really would like the ATi or fgrlx driver to work.

---

### Post by SVFUSiON on 2007-01-16
*BUMP* :rolleyes:

---

### Post by mrfuzzemz on 2007-01-16
> it just locks up on boot when I dpkg-reconfigure xserver-xorg

are you doing this with sudo in front?

I'm not sure why it might lock-up, but you be sure to be using:

```
sudo dpkg-reconfigure xserver-xorg
```

If it still doesn't seem to work be sure that you are doing everything the [Ubuntu ATI howto]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") says

---

