---
title: "The last attempt...to get Direct Rendering to work."
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by nomiK on 2007-02-20
Hi,

I have been trying for a while to get direct rendering to work on a AIW Radeon 9800 Pro. I have a bunch of errors in my log file 
**/var/log/Xorg.0.log**
> (II) Open ACPI successful (/var/run/acpid.socket)
(II) APM registered successfully
(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!    *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available    *
(WW) fglrx(0): ***********************************
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(**) fglrx(0): Video overlay enabled on CRTC1
(==) RandR enabled
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
AUDIT: Tue Feb 20 09:52:33 2007: 4183 X: client 1 rejected from local host
Error in "atiddxMiscUpdateFile" -4 
Error in "atiddxMiscUpdateFile" -4 
(II) 3rd Button detected: disabling emulate3Button


It would be nice if someone could go through this and tell me why direct rendering is disabled.

Thanks.

---

### Post by po0f on 2007-02-20
nomiK,

I don't own any ATi cards, but isn't the 9550 supported by the open drive "radeon"?  And you can ignore the errors about the "wacom" device.

---

### Post by nomiK on 2007-02-20
I dont understand what you mean, I am using 9800?

Also here is my **xorg.conf**
> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "VA712b"
	HorizSync    30.0 - 65.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "VA712b"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection



---

### Post by po0f on 2007-02-20
nomiK,

Oh yeah, sorry.

Drive this for a device section:

```
[font="Courier New"]Section "Device"
Identifier "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
    Driver "radeon"
    #Option "VideoOverlay" "on"
    #Option "OpenGLOverlay" "off"
    BusID "PCI:1:0:0"
EndSection[/font]
```

Back up xorg.conf before trying this:

```
[font="Courier New"]$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak[/font]
```

---

### Post by nomiK on 2007-02-20
I just tried the radeon drivers and nothing seemed to have changed. Direct rendering is still  a "no"

---

### Post by Maestro23 on 2007-02-20
> **nomiK said:**
> I just tried the radeon drivers and nothing seemed to have changed. Direct rendering is still  a "no"

How did you install the driver for your card?  Follow a How-To or use the Envy script?

---

### Post by ashmew2 on 2007-02-20
I WOULD suggest Envy script , which u can get by clicking [Here]("http://albertomilone.com/nvidia_scripts1.html")

When u run envy , first make sure to backup xorg.conf and then when it starts , first choose UNINSTALL ATI DRIVER.

Then after it does its thingy , INSTALL ATI DRIVER.

---

### Post by nomiK on 2007-02-20
ok I went ahead and used envy, it installed the newest drivers 8.33.6 and i still get no direct rendering. I am now going to try older drivers....

---

### Post by nomiK on 2007-02-20
Legacy drivers dont work either...I just dont understand how such a popular card wont work, ive been working on this for over 2 weeks. :(

---

### Post by DivineOmega on 2007-02-20
The Envy scripts appear to compile the driver as a kernel module... which means whenever a new kernel update is released X will die and the script will have to be re-run if I'm not mistaken.

This is how I installed the drivers for my laptop: [http://divineomega.co.uk/linux/how-to-install-ati-graphics-drivers-in-ubuntu/](http://divineomega.co.uk/linux/how-to-install-ati-graphics-drivers-in-ubuntu/)

---

### Post by Shatrat on 2007-02-20
"I just dont understand how such a popular card wont work"
well, ATI puts very little effort into their linux/unix drivers or documenting their hardware so that open source drivers will work.  
Supposedly AMD/ATI is trying to stage a rally and catch up to nvidia and intel on their multi platform support but that isnt gonna help you for quite some time.  I finally just gave up on my ati card and replaced it with an nvidia.

If it makes you feel better, it took me more than 2 weeks to get my 9600pro going the first time, and the last attempt is always the first one that works!

---

### Post by aktiwers on 2007-02-20
I have had simulair problems on my old ATI. Sometimes I could just turn the direct rendering on manually with this program:

```
sudo apt-get instal drconf
```

Then run it:

```
driconf
```

in there you should be able to enable direkt rendering..  but its not always it worked for me.. but give it a try.

---

### Post by nomiK on 2007-02-20
On starting DRIconf:
> Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode.

On adding a device in DRIconf:
> Screen "0" is not direct rendering capable.

Also, this uses xfree86, i though ubuntu 6.10 was using xorg

---

### Post by pljones on 2007-02-21
Can I just ask if you've disabled compositing?  You should have this in your /etc/X11/xorg.conf somewhere:
```
Section "Extensions"
        Option      "Composite" "Disable"
EndSection
```
Of course, then you can't use a compositing window manager.

---

### Post by nomiK on 2007-02-21
been there,, done that....

---

