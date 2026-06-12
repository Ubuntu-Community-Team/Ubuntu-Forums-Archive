---
title: "ATI Driver install for WoW on 7.04"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Mystic_Viper on 2007-08-02
[CENTER]There are threads everywhere and they start off helpful but then they get specific for one computer and i get lost, so this ones for the Toshiba A75 (S231) people.[/CENTER]

I've been with windows forever, even 3.x, but I always wanted to do something else. I learned DOS when win95 came out, C++ and BASIC when winME started popping up, even played with Caldera KDE (I think thats what it was), but now I am looking for more control. I read somewhere a article about someone taking a Toshiba A75 and Dual Booting Ubuntu&Windows XP, then installing World of Warcraft and getting 40+ FPS in Ubuntu over 17+ in Windows XP. So i read up on the process and tries my hand at it. Alas i can't seem to get my ATI drivers to install, i have a ATI Mobility Radeon 9000 IGP (it has a Radeon 9100 chipset) that shares 128mb of my 1024mb ram, I want to install the ATI Proprietary drivers but i dont know how, or i want to install the Mesa 7.0 OpenGL Drivers, or some thing or someone help me find a thread that has done this already. 

When i launch the ATI install software i get:

mystic@Isis:~$ sh /home/mystic/ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8...................................................................................................................................
..........................................................................................................................................................
..........................................................................................................................................................
..............................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: **_Syntax error: Bad substitution_**
Removing temporary directory: fglrx-install

I've tried to allow read/write access and "allow execution" but i still get the same error under my login and the root login. I dont know my way around the terminal so i can log in to the root account and move the the containing folder and run:

chmod +x ati-driver-install....
sudo ./ati-driver-install...

And yes i want to know how but i cant find a forum for that(I understand DOS so the terminal window can be that difficult to master)

The MESA 7.0 installation confuses me with its .tar compile decompile installation, and i have not found a forum for that that can meet my level of knowledge and usually its just one step or the setup is for Edgy or Dapper, or worse yet some super X9-Billion ATI card thats not out yet.

Ubuntu's Application installer provides a xorg-driver-fglrx package for ATI cards but then i can't get the setup to make a difference. I've followed the community guide to the best of my ability's but i cant seem to get it right and twice I've crashed the GUI.
[URL="https://help.ubuntu.com/community/WorldofWarcraft"]
_https://help.ubuntu.com/community/WorldofWarcraft_ [/URL]

Like I said all I want is WoW to run better than Windows. I think the Hardware 3D Acceleration is not working cause OpenGL can't find it. Alas, I don't know how to check for this, or i could give you more. WoW does run, under Wine's DirectX and D3D modes i get 7 FPS, and under OpenGL I get 3 FPS. But in Windows I can get 17 FPS and 50+ if i look up at nothing.

I've managed some bug fixes on my own(the APIC boot error, crashing my Ubuntu install from a bad modification to the Xorg.conf file, and much more) there is no critical files on this computer (except the 2 hour WoW Install) and most problems i can fix from windows if i can't get the GUI to load. I ran with Ubuntu 7.04 because it saw almost all my hardware over the 6.10 and 6.04 versions. If you can point me to a new horizon or find my critical flaw i would be ever so grateful and I can stop writing long explanations.

---

### Post by w4ett on 2007-08-03
The proprietary fglrx driver only supports the ATI Radeon 9500 cards/chipsets and above.  You will have to use the xorg driver ati.

If you are using the Vesa driver you will have to reconfigure your xorg.conf by typing in the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select[COLOR="Red"] ati[/COLOR] as your driver.  This will enable some 3D rendering.....I get about 850-900 fps in glxgears on my 9200 card

---

### Post by Mystic_Viper on 2007-08-03
Failure, at least the GUI still works....

Now WoW gives a error "WoW was unable to start up 3D acceleration"

I've seen it before but i knew what the problem was.

Now i dont, oh hum.

D3D and DrirectX still work but OpenGL keeps giving me an error.

---

### Post by Mystic_Viper on 2007-08-03
And it killed my GUI, very messed up

---

### Post by Mystic_Viper on 2007-08-03
Ok, fixed the GUI, but i lost my enhanced desk top(darn) and wow still wont boot

xorg.conf states

[I]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection[/I]


Going to add the commands fron the community web page, and try again.

---

### Post by Mystic_Viper on 2007-08-03
Well 6 GUI crashes later, and still nuthin. I'll quit for the day and wait for another idea (or to be told what I'm doing wrong)

---

### Post by w4ett on 2007-08-03
Post the output of:
```

lspci

glxinfo

glxgears
```

and let's see what your exact chipset is and what direct rendering is doing.

Plus...I once had a MOBO that no matter what I tried, I couldn't get 3D to work unless i added the following to the device section:

> Identifier "ATI Radeon 9200SE"
Driver "ati"
BusID "PCI:1:0:0"
[COLOR="Red"]VideoRam 65536
Option "BusType" "PCI"[/COLOR]

---

### Post by Mystic_Viper on 2007-08-04
After every GUI crash i had to go back and restore the xorg.conf with a backup of one before I ran the command line:

*sudo dpkg-reconfigure -phigh xserver-xorg*

So I ran that command first, rebooted, and ran the three commands you just gave me:

***lspci***

[I]mystic@Isis:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
[/I]

***glxinfo***

[I]mystic@Isis:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None[/I]

***glxgears***

[I]mystic@Isis:~$ glxgears
2671 frames in 5.2 seconds = 515.715 FPS
2640 frames in 5.1 seconds = 519.452 FPS
2640 frames in 5.1 seconds = 520.944 FPS
2640 frames in 5.1 seconds = 520.282 FPS
2640 frames in 5.1 seconds = 520.611 FPS
2640 frames in 5.1 seconds = 520.246 FPS
2640 frames in 5.1 seconds = 520.905 FPS
2640 frames in 5.1 seconds = 517.337 FPS
2640 frames in 5.1 seconds = 516.402 FPS
2640 frames in 5.1 seconds = 517.729 FPS
2640 frames in 5.2 seconds = 506.782 FPS
[/I]
[SIZE="5"]***_LIES!!!_***[/SIZE]

Looks more like 3 FPS, or I don't understand what 515+ FPS means.

To reiterate my laptop has a ATI Mobility Radeon 9000 IGP GFX Card and it uses a Radeon 9100 chip set.

The enhanced desktop wont work any more (Why? No its not important but i want to know) and i think the screen saver crashes when it tries to go back to the desk top, not critical but FYI. Any thing else you need to know just ask.

If its possible I would like to try to reformat the Linux partition and reinstall 7.04, only because I have done so much to try to get the card to work that have lost track of failed modifications, its not important but i would like to know for a last ditch option. The modifications only concern the WINE REG EDIT, WoW WTF.CFG, xorg.conf, just the stuff the community doc at the top told me to do.

---

### Post by w4ett on 2007-08-04
The line here:

> 
glxinfo

mystic@Isis:~$ glxinfo
name of display: :0.0
display: :0 screen: 0
[COLOR="Red"]direct rendering: No[/COLOR]
server glx vendor string: SGI
server glx version string: 1.2

Tells me you do not have 3D rendering enabled.   Why not post your xorg.conf too...easiest way is:

```
cat  /etc/X11/xorg.conf
```

'cat' is the equivalent of the 'list' command in Dos.

You might be missing the load "dri" like here:

> Section "Module"
        Load    "bitmap"
        Load    "ddc"
[COLOR="Red"]        Load    "dri"[/COLOR]
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection


---

### Post by Mystic_Viper on 2007-08-04
I knew you would be needing that, lazy me.

[I]mystic@Isis:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        **Load    "dri"**
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection



Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection


**_## This is my own modification_**
Section "DRI"
        Mode    0666
EndSection
[/I]
The WoW forum wants me to add:

 Section "Device"
   Identifier  "aticonfig-Device[0]"
   Driver      *"fglrx"* 
[I]   Option       "Capabilities" "0x00000800"
   Option       "UseFastTLS" "off"
   Option       "KernelModuleParm" "locked-userpages=0"[/I]
 EndSection

Changing the "DRIVER" to "fglrx" and adding the next 3 lines but i get Ubuntu's "blue screen of death" when the GUI tries to load. I see the "DRI" line but what do you want from it?

---

### Post by w4ett on 2007-08-04
> Section "Module"
[COLOR="Red"]Load "i2c"[/COLOR]
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Try deleting the Load "i2c"  The next section is ok....it is normally loaded by the default ati driver from the live cd:

> Section "DRI"
Mode 0666
EndSection

Additionally, you can load the live cd, copy the default xorg.conf to you HDD or flash drive and replace it.

---

### Post by Mystic_Viper on 2007-08-05
[I]mystic@Isis:~$ glxgears
2673 frames in 5.1 seconds = 522.332 FPS
2640 frames in 5.1 seconds = 521.365 FPS
2640 frames in 5.1 seconds = 522.565 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 17862 requests (35 known processed) with 0 events remaining.[/I]

Still looks like 3 FPS. 

[I]Identifier "ATI Radeon 9200SE"
Driver "ati"
BusID "PCI:1:0:0"
[U]VideoRam 65536
Option "BusType" "PCI"[/U][/I]

Your previous quote said you needed this for your card to work, but my card shares the RAM and in Windows i know it uses 128mb from my 1024mb of SDRAM (the computer came with 512mb but i upgraded it with a 1024mb stick and the ATI card automatically went from 64mb to 128mb, and I see the RAM reroute in the boot screen cause it states "*896mb tested + 128 shared*"). It looks like its set for 64mb in  that command, what would be the 128mb equivalent and would it be safe to implement it?

---

### Post by Mystic_Viper on 2007-08-05
And in World of Warcraft it still cant start the 3D Acceleration

---

### Post by w4ett on 2007-08-05
> **Mystic_Viper said:**
> [I]mystic@Isis:~$ glxgears
2673 frames in 5.1 seconds = 522.332 FPS
2640 frames in 5.1 seconds = 521.365 FPS
2640 frames in 5.1 seconds = 522.565 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 17862 requests (35 known processed) with 0 events remaining.[/I]

Still looks like 3 FPS. 

[I]Identifier "ATI Radeon 9200SE"
Driver "ati"
BusID "PCI:1:0:0"
[U]VideoRam 65536
Option "BusType" "PCI"[/U][/I]

Your previous quote said you needed this for your card to work, but my card shares the RAM and in Windows i know it uses 128mb from my 1024mb of SDRAM (the computer came with 512mb but i upgraded it with a 1024mb stick and the ATI card automatically went from 64mb to 128mb, and I see the RAM reroute in the boot screen cause it states "*896mb tested + 128 shared*"). It looks like its set for 64mb in  that command, what would be the 128mb equivalent and would it be safe to implement it?



For 128 Mb it will be:

> VideoRam 131072

Your card will probably work without forcing it into "BusType" "PCI"....try it without and see what you get...also verify your bios video settings....like shared memory settings and bus type...and AGP type (4x/8x) and make sure all are correct.

---

### Post by Mystic_Viper on 2007-08-05
Bios wont let me configure the ATI card, or i see no option for it, and the *glxinfo* still says that there is no direct rendering.....shouldn't it say yes? I swear I'll get this running if its the last thing i do.

[I]mystic@Isis:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
[/I]
[I]mystic@Isis:~$ glxgears
2671 frames in 5.0 seconds = **529.529 FPS**
2760 frames in 5.2 seconds = **529.184 FPS**
2760 frames in 5.2 seconds = **529.498 FPS**
2760 frames in 5.2 seconds = **529.263 FPS**[/I]

Anyway the line for the *BUS SET PCI *made it worse but i think the RAM 130000 did a little, I don't know.

WoW will run in 3D3 mode but it still whines about not being able to start up 3D Acceleration.

---

### Post by Mystic_Viper on 2007-08-15
A problem so huge it killed a forum thread.....
*bump

---

### Post by stchman on 2007-08-15
> **Mystic_Viper said:**
> [CENTER]There are threads everywhere and they start off helpful but then they get specific for one computer and i get lost, so this ones for the Toshiba A75 (S231) people.[/CENTER]

I've been with windows forever, even 3.x, but I always wanted to do something else. I learned DOS when win95 came out, C++ and BASIC when winME started popping up, even played with Caldera KDE (I think thats what it was), but now I am looking for more control. I read somewhere a article about someone taking a Toshiba A75 and Dual Booting Ubuntu&Windows XP, then installing World of Warcraft and getting 40+ FPS in Ubuntu over 17+ in Windows XP. So i read up on the process and tries my hand at it. Alas i can't seem to get my ATI drivers to install, i have a ATI Mobility Radeon 9000 IGP (it has a Radeon 9100 chipset) that shares 128mb of my 1024mb ram, I want to install the ATI Proprietary drivers but i dont know how, or i want to install the Mesa 7.0 OpenGL Drivers, or some thing or someone help me find a thread that has done this already. 

When i launch the ATI install software i get:

mystic@Isis:~$ sh /home/mystic/ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8...................................................................................................................................
..........................................................................................................................................................
..........................................................................................................................................................
..............................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 165: **_Syntax error: Bad substitution_**
Removing temporary directory: fglrx-install

I've tried to allow read/write access and "allow execution" but i still get the same error under my login and the root login. I dont know my way around the terminal so i can log in to the root account and move the the containing folder and run:

chmod +x ati-driver-install....
sudo ./ati-driver-install...

And yes i want to know how but i cant find a forum for that(I understand DOS so the terminal window can be that difficult to master)

The MESA 7.0 installation confuses me with its .tar compile decompile installation, and i have not found a forum for that that can meet my level of knowledge and usually its just one step or the setup is for Edgy or Dapper, or worse yet some super X9-Billion ATI card thats not out yet.

Ubuntu's Application installer provides a xorg-driver-fglrx package for ATI cards but then i can't get the setup to make a difference. I've followed the community guide to the best of my ability's but i cant seem to get it right and twice I've crashed the GUI.
[URL="https://help.ubuntu.com/community/WorldofWarcraft"]
_https://help.ubuntu.com/community/WorldofWarcraft_ [/URL]

Like I said all I want is WoW to run better than Windows. I think the Hardware 3D Acceleration is not working cause OpenGL can't find it. Alas, I don't know how to check for this, or i could give you more. WoW does run, under Wine's DirectX and D3D modes i get 7 FPS, and under OpenGL I get 3 FPS. But in Windows I can get 17 FPS and 50+ if i look up at nothing.

I've managed some bug fixes on my own(the APIC boot error, crashing my Ubuntu install from a bad modification to the Xorg.conf file, and much more) there is no critical files on this computer (except the 2 hour WoW Install) and most problems i can fix from windows if i can't get the GUI to load. I ran with Ubuntu 7.04 because it saw almost all my hardware over the 6.10 and 6.04 versions. If you can point me to a new horizon or find my critical flaw i would be ever so grateful and I can stop writing long explanations.

Ok, to install 3D acceleration for ATI in Ubuntu do one of the following:

A.  Enable restricted driver in Feisty
B.  Install ATI driver using Envy

No reason to make matters more complex than they really are.

---

### Post by w4ett on 2007-08-15
> **stchman said:**
> Ok, to install 3D acceleration for ATI in Ubuntu do one of the following:

A.  Enable restricted driver in Feisty
B.  Install ATI driver using Envy

No reason to make matters more complex than they really are.

The OP has as a video card:

> 01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]

fglrx is only compatible with ATI Radeon 9500 cards/chipsets and above....the correct driver is xorg-driver-ati

I quote from:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

> Prerequisites

Make sure the following things are true about your video card:

    *

      It is a 'Radeon' card
    *

      The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.


---

### Post by dougfractal on 2007-08-18
JesseEklund  Jesse
[http://ubuntuforums.org/showthread.php?t=527529](http://ubuntuforums.org/showthread.php?t=527529)
> Whenever i start WoW i get this error:

World of Warcraft was Unable to start up 3D Acceleration
he's has WoW running but a bit choppy (using intel 900). check his thread out it might help.



I'm  tring to collect info on ati/radeon and intel cards

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

