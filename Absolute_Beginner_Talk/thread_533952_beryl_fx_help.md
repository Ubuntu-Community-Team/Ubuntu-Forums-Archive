---
title: "beryl fx help"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Caton420 on 2007-08-24
iv been hearing about these effects and decided to dl it, well i dl it open it, it goes to my tray, and nothing changed... i right click it to see settings manager, it seems all is on, but idk
thx!

---

### Post by Vadi on 2007-08-24
What you want is Compiz Fusion. Beryl = Compiz Fusion now.

Hold down ctrl, alt and press on your mouse and move it about. Windows also will wobble when moved... well, there's a ton of effects really.

---

### Post by Caton420 on 2007-08-24
how do i aquire this?/use it

---

### Post by sailor2001 on 2007-08-24
alt/f2  and type:   compiz --replace    however why don't you open the manager (from synaptics) and set it up they way you want?  Manager should be in system/preferences

---

### Post by Vadi on 2007-08-24
> **Caton420 said:**
> how do i aquire this?/use it

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Also visit compiz.org, that's the official site of it.

---

### Post by Caton420 on 2007-08-24
> caton420@caton420-laptop:~$ compiz --replace
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded" when i try to run

---

### Post by Vadi on 2007-08-24
Install Compiz then. Beryl is old.

---

### Post by Caton420 on 2007-08-24
yeah that was dumb lol but prolly the last one
```
caton420@caton420-laptop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
caton420@caton420-laptop:~$ 

```

---

### Post by Caton420 on 2007-08-24
bump

---

### Post by mysticmatrix on 2007-08-24
Please paste the output of following command:

```
lspci
```

and 

```
glxinfo
```

---

### Post by Caton420 on 2007-08-24
lspci brngs up
> caton420@caton420-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
caton420@caton420-laptop:~$ 

and glxinfo brings up
> caton420@caton420-laptop:~$ glxinfo
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
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
caton420@caton420-laptop:~$ 



---

### Post by mysticmatrix on 2007-08-24
Your graphics card is ATI Radeon Xpress 200M. It looks like that you don't have drivers from ATI installed.
Can you provide me with output of 

```
 cat /etc/X11/xorg.conf
```

---

### Post by Caton420 on 2007-08-24
here ya go and thanks alot for ur time to btw
> caton420@caton420-laptop:~$ cat /etc/X11/xorg.conf

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

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
        Driver      "ati"
        BusID       "PCI:1:5:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
        Monitor    "Generic Monitor"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x800"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

caton420@caton420-laptop:~$ 


---

### Post by mysticmatrix on 2007-08-24
Hmnn this is odd. It seems like you have installed the ATI Drivers but still your system is not recognising it somehow.

The following steps might resolve it:

1) Reboot your system
2) In Terminal, type
```
glxinfo | grep 'direct rendering'
```

If it says Yes, Proceed on to [installing XGL from here ]("https://help.ubuntu.com/community/CompositeManager/Xgl")and then start compiz.

ELSE if you get no

3) Backup your xorg.conf first.

```
sudo cp /etc/X11/xorg.conf /etc/X11/etc.conf_backup
```

4) Then do

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

It will ask few simple questions. When in doubt, simly accept the default settings. Make sure to select driver as 'ati'
5) Press Ctrl+Alt+BackSpace

This will fix your problem and then proceed to step two.

If step 2, still says no, reply back.

And if in any case you mess up completely and get no GUI, do this
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/etc.conf
```

Please respond what you get out of this. Also recommend you to note this on a piece of paper and then proceed.

---

### Post by Caton420 on 2007-08-25
it still says no and now 'nautalius' (sp?) dosent work (im not sure if this is nautilius or not but i also have no desktop icons anymore) help please

---

### Post by Caton420 on 2007-08-25
also for the record i get this message when it says no
> caton420@caton420-laptop:~$ glxinfo | grep 'direct rendering'
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
caton420@caton420-laptop:~$ 



---

### Post by mysticmatrix on 2007-08-25
Till which point did you worked out??

---

### Post by Caton420 on 2007-08-25
> It will ask few simple questions. When in doubt, simly accept the default settings. Make sure to select driver as 'ati'
5) Press Ctrl+Alt+BackSpace

This will fix your problem and then proceed to step two.

If step 2, still says no, reply back.
nautilus seems to be back after reboot by the way

---

### Post by mysticmatrix on 2007-08-25
I think I'm close to the problem:KS. Will you please post me output of this command again:

```
 cat /etc/X11/xorg.conf 
```

---

### Post by Caton420 on 2007-08-25
whoa thats a bigin
```
caton420@caton420-laptop:~$  cat /etc/X11/xorg.conf
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
        Load    "dri"
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
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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

Section "DRI"
        Mode    0666
EndSection
caton420@caton420-laptop:~$ 

```

---

### Post by mysticmatrix on 2007-08-25
Ok here it goes. This should do it

1) As always, make a backup.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup2
```

2) Then in terminal type

```
gksudo gedit /etc/X11/xorg.conf
```

3) Now replace this section of file
```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "ati"
        BusID           "PCI:1:5:0"
EndSection
```

by this

```
Section "Device"
	Identifier       "ATI Radeon X200M"
	Driver		 "fglrx"
	Option		 "VideoOverlay" "on"
	Option		 "OpenGLOverlay" "off"
EndSection
```

4) Ctrl+Alt+Backspace and then relogin.
5) See if output of

```
glxinfo | grep 'direct rendering'
```

is true
Please tell if this works or not.
---------------------------------------------------------------------------
If you are unable to see login screen(GUI) at any point, press Ctrl+Alt+F1,login, and restore your xorg.conf by command I gave before and reboot.

---

### Post by Caton420 on 2007-08-25
well at least it did somthing... and i know what the issue is...
it went to DOS looking screens with a log file it read
the screen "boot screen" is looking for the "default video card" one.
thank god i decided to dual boot with xp this time :lolflag:

---

### Post by Caton420 on 2007-08-25
also after this i could login my caton420 name and pass at a terminal, then i just sorta forgot to check if it changed

---

### Post by mysticmatrix on 2007-08-25
Well as I have screwed up, you can always restore from backup you made.

1) Start Ubuntu
2) When boot process finishes, press Ctrl+Alt+F1.
3) You will get a terminal sorta thing. Login by your password and user name.
4) Type

```
sudo mv /etc/X11/xorg.conf_backup2 /etc/X11/etc.conf
```

5) Reboot.

Sorry I wasted too much of your time and took you nowhere. I guess you can try at Desktop effects forum. :confused:

---

### Post by Caton420 on 2007-08-25
naw its cool i will try there 2morrow its bed time
hey wasting my time!? are you serious i learned so much, especially about backups:)

---

### Post by Vadi on 2007-08-25
I had that error too (unable to start compiz on this machine, bla blah), it turned out that I installed ATI drivers by accident. Which was a bad thing. I uninstalled them, and my compiz worked fine.

Here's the thread that I had on the compiz forums about this: [http://forum.compiz-fusion.org/showthread.php?t=3204](http://forum.compiz-fusion.org/showthread.php?t=3204)

Maybe it'll help.

---

