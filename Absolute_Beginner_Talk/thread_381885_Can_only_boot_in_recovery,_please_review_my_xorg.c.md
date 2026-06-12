---
title: "Can only boot in recovery, please review my xorg.conf"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Mischief on 2007-03-11
Hi,

After a long time of trial and error I finally got Ubuntu up and running in recovery mode using alternate installer i386 6.10.

The problem I have with the Live CD was that my ATI Mobility Radeon X700 wouldn't work properly.

After installing via alternate installer, I used the following guide:
[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

In the terminal, by booting in recovery mode, I installed the drivers using:

> sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

startx

Ubuntu booted just fine, great! 
Then when I tried booting "normally", the screen on the laptop goes white and the Ubuntu logo fades away, the the system is dead.

I reviewed my xorg.conf and found the following:

> Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "ati" [COLOR="Red"]*note[/COLOR]
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

[COLOR="Red"]* [/COLOR]I've tried "ati", "vesa" and "radeon" with the same "white screen" result.

Should there really be two sets of " Section "Device" "?

Any other suggestions what could be wrong. I feel that I'm very very close of getting this up and running, just need the final push so to speak.

Also, I'd like to thank all the people in here who does a great job helping people like me out ;)

**My complete xorg.conf**

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
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
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
	Option	    "XkbOptions" "lv3:ralt_switch"
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
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 84.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
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

---

### Post by Najand on 2007-03-11
Do you want to boot using live CD or you have installed ubuntu on your computer?

---

### Post by Mischief on 2007-03-11
No, I already installed Ubuntu in "text mode" via Alternate i386 6.10 installer.

All I want is to be able to do is to boot into Ubuntu in the ordinary way. Right now I have to boot in "recovery mode" startx.

---

### Post by Najand on 2007-03-11
Well,  let us see... If you have been able to fix it using the recovery mode, you can use the same way to fix it in your normal boot.
Can you try the following:
1. Boot in the normal mode.
2. When it failed to load the X, then puch Ctrl+Alt+F1 to go to the terminal.
3. Go through the same way you used to fix it previously.
4. After you finished, don't use "startx". Just Push Ctrl+Alt+F7 to go back to the white screen.
5. Push Ctrl+Alt+Backspace to restart X again
If it works, then there is no need to go trough the xorg.conf, if it doesn't we can find other ways to fix it. ;)

---

### Post by soul814 on 2007-03-11
I don't think there is an error with your xorg configure. Beryl is in beta and I heard the latest version of beryl gives a white screen when you load it. I'm new to linux so I don't know much but I'm guessing once you boot your loading up beryl and xgl. What I do to avoid this white screen problem is load it after I boot. 

[http://forum.beryl-project.org/viewtopic.php?f=36&t=4692](http://forum.beryl-project.org/viewtopic.php?f=36&t=4692)

---

### Post by wpshooter on 2007-03-11
MIschief:

If you went to all of that trouble to install the fglrx video drivers, then why would you put "ATI", "VESA", or "RADEON" in the driver parameter of xorg.conf instead of **fglrx** ?

---

### Post by Mischief on 2007-03-11
> **wpshooter said:**
> MIschief:

If you went to all of that trouble to install the fglrx video drivers, then why would you put "ATI", "VESA", or "RADEON" in the driver parameter of xorg.conf instead of **fglrx** ?
I just read that alot of ATI radeon users were albe to boot after switching from "ATI"->"VESA" or "radeon". Since I was unable to boot after installing fglrx, I thought this was the problem. I never put "ati" there, it was there from the start, even after installing fglrx.
I've made no changes to xorg.conf, beside loading the backup I took of xorg.conf after installing fglrx.

Should I change "ati" to "fglrx"?


> **Najand said:**
> MIschief:
Well, let us see... If you have been able to fix it using the recovery mode, you can use the same way to fix it in your normal boot.
Can you try the following:
1. Boot in the normal mode.
2. When it failed to load the X, then puch Ctrl+Alt+F1 to go to the terminal.
3. Go through the same way you used to fix it previously.
4. After you finished, don't use "startx". Just Push Ctrl+Alt+F7 to go back to the white screen.
5. Push Ctrl+Alt+Backspace to restart X again
If it works, then there is no need to go trough the xorg.conf, if it doesn't we can find other ways to fix it.


The thing is that the laptop is completely dead when the white screen shows. No ALT+combination will work. Have to power off the laptop to be able to do any action. I can see the Ubunto loader logo slowly fade away and then the screen turns white.


What I still don't get is why I can boot in recovery mode to terminal, startx and then it works fine but that I'm unable to boot in normal mode where I get the white screen. In recovery mode I don't do any changes to xorg.conf, I just stype startx in terminal.

Thanks for the quick help by the way.

---

### Post by wpshooter on 2007-03-11
Yes, try putting in fglrx in that parameter.

Go into recovery mode and edit the xorg.conf file and make sure you save the change to the file.  Might not be a bad idea to save the originial file before making the change to another name **FIRST**.

I am believing that this is going to fix your problem.

Good luck.

---

### Post by Mischief on 2007-03-11
Thanks but I ended up with the same fading Ubuntu logo into white. I did like you said and changed "ati" to "fglrx" but the system behaved like it did when "ati" was there.

Any outher suggestions? I'm browsing every related topic I can find but come up with nothing.

---

### Post by Mischief on 2007-03-12
After another night of thinking and widescreen sprung to mind.
Do I have to define any settings for widescreen in the xorg.conf?

Can I install other drivers that might work better?

---

### Post by Mischief on 2007-03-14
Nope, that didn't do it either.

Recover mode works great except for the limitations in functionality.
Can someone explain the difference between booting in recovery and in normal mode?

Which settings are different?

Come on people, someone must know how to do this, I cannot be the the only Acer Travelmate 8100 user.

Thanks in advance!

---

