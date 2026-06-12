---
title: "Cannot Enable ATI Restricted Driver"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Holy Knight on 2007-09-04
Hello People.Once again I have a problem.
I have an ATI 9250 graphic card and I wanted to install Compiz Fusion.But according to a howto I had to enable its restricted driver from you-know-where.But when I try to open it it says that My Hardware does not need a restricted driver.I decided to ignore it and continued creating XGL for Gnome.

It was nearly successful,but when I change the session to Gnome with XGL the frame rate was horrifyingly slow:confused:.I suspected that the ATI driver must be causing the problem.

So can anyone tell me the alternate of installing the restricted driver of ATI 9250.

Thanks

---

### Post by nosrednaekim on 2007-09-04
restricted-manager probably thinks that your card is fully supported by the open drivers. OR... maybe that is too new of a card. Have you bought it in the past 6 months?

---

### Post by swisscow on 2007-09-04
I believe it is the fglrx driver. Try this (from the sticky)

   Update package list and upgrade any packages needed.
      

      ```
sudo apt-get update
      sudo apt-get dist-upgrade
```

   5. Install fglrx closed source driver for ATI video cards.
     
     ```
 sudo apt-get install xorg-driver-fglrx
```

   6. Update loaded modules.

  ```
    sudo depmod -a
```

   7. Configure /etc/X11/xorg.conf

```
      sudo aticonfig --initial
      sudo aticonfig --overlay-type=Xv
```

   8. Reboot


Check the xorg.conf file ```
gksudo gedit /etc/X11/xorg.conf
```

Make sure in the section device you have the drive as 'fglrx'

Also make sure you have

```
Section "Extensions" 
Option "Composite" "0" 
EndSection 
```

at the end of the file.

While in the file check that the screen section picks upi the correct device and monitor, similarly with the server section. I've posted mine if that helps - note I DO NOT USE XGL

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
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
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#	Identifier  "stylus"
#	Driver      "wacom"
#	Option	    "Device" "/dev/input/wacom"
#	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Identifier  "eraser"
#	Driver      "wacom"
#	Option	    "Device" "/dev/input/wacom"
#	Option	    "Type" "eraser"
#	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Identifier  "cursor"
#	Driver      "wacom"
#	Option	    "Device" "/dev/input/wacom"
#	Option	    "Type" "cursor"
#	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
#EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc M22 [Radeon Mobility M300]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc M22 [Radeon Mobility M300]"
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

Section "DRI"
	Mode         0666
EndSection

Section "Extensions" 
Option "Composite" "0" 
EndSection 
```

I recommend a reboot if you make any changes. I also recommend making not of any changes or a backup of the xorg using

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bup
```

which you can then restore if it all stuffs up.

---

### Post by Holy Knight on 2007-09-05
> **nosrednaekim said:**
> restricted-manager probably thinks that your card is fully supported by the open drivers. OR... maybe that is too new of a card. Have you bought it in the past 6 months?

Its not new....almost 2 years old.

---

