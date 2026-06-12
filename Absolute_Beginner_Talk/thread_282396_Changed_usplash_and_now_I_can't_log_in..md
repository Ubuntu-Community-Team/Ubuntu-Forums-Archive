---
title: "Changed usplash and now I can't log in."
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-10-22
I am running Ubuntu 6.06.1 but I have also install kde (kubuntu-desktop).  It's been working fine for the past few days, but I noticed that the bootsplash has changed from the brown Ubuntu to the blue Kubuntu.

I wanted to change it back to the brown Ubuntu.  After some searching on the forum, I came accross [http://doc.gwos.org/index.php/Different_usplash]("this wiki").

I followed it to the letter and it reported no errors.

I then wanted to install SuperKaramba, so I did so from the respositories.

After installation, nothing seemed to 'appear' on the desktop or in Kmenu, so I figured I should re-start X.  So I pressed ctrl+alt+backspace.  I did not log-out before doing this.  I think this may have been my mistake.  The login screen came up but I could not log back in.  I tried every session with the same result:  after entering my username+password, the brown Ubuntu login screen would disappear, the screen would go blank, then the F1 console (tty1) would appear with a login prompt which, after a few seconds (without touching anything), would revert back to the brown Ubuntu login screen.  Even the Failsafe GNOME and Failsafe Terminal sessions would not allow me to login.  Every time I get the tty1 console -> brown Ubuntu login screen thing happening.

Is there a simple fix for this?  I tried re-doing the above mentioned link but this time reverting back to kubuntu, again no joy.  I can't seem to login no matter what I try :(

Can anyone please help?

P.S.  I've attached my /etc/X11/xorg.conf file below (in case it's any help).  Apologies for the resulting length of the post.

My /etc/X11/xorg.conf file:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	Load  "type1"
	Load  "vbe"
	Load  "GLcore"
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
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
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
	Identifier  "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver	    "ati"
	BusID	    "PCI:1:0:0"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "AccelMethod" "XAA"		#Choices are XAA or EXA.  XAA is more stable
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes	"1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection
```

---

