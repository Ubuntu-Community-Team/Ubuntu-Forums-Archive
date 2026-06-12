---
title: "Installing NVIDIA Graphics Driver from &quot;Restricted Drivers&quot; does not work"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by TMcKSmith on 2008-04-03
I am on a Dell Latitude D620 laptop running KUBUNTU, hoping to get a Dual-Screen "Big Desktop" setup working.  When I go into the "Restricted Drivers", its lists:
NVIDIA accelerated graphics driver (latest cards)
Firmware for Broadcom 43xx chipset family

I successfully installed the Broadcom firmware via the Restricted Drivers manager, and it worked great - my wireless is up and running.  However, when I install the NVIDIA driver, downloads/installs...and then says that I need to reboot.  After I reboot, it does not load the X-Server.  I had to replace a backup xorg.conf with the current in order to get it up and running again.  Am I doing something wrong?  Thanks.

---

### Post by hessiess on 2008-04-03
witch card exactily?, you may need to get the driver form nvidias website as the one in the repo isnt always up to date with the newist hardwere.

---

### Post by TMcKSmith on 2008-04-03
how do I check the exact card model?  Thanks.

---

### Post by hessiess on 2008-04-03
run 'lspci' in the terminal an look for a line like this

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

---

### Post by TMcKSmith on 2008-04-03
this is what I'm getting:
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

---

### Post by hessiess on 2008-04-03
did you use nvidia-glx or nvidia-glx-new?

try

```
sudo apt-get install nvidia-glx
```

---

### Post by TMcKSmith on 2008-04-03
well, when I went into "Restricted Drivers" it automatically installed for me...
when I checked in Adept it said nvidia-glx-new was installed

---

### Post by hessiess on 2008-04-03
try nvidia-glx, see edited post above

---

### Post by TMcKSmith on 2008-04-03
Okay, I uninstalled the nvidia-new driver, and installed nvidia-glx.  When I go into "Restricted Drivers" it says the NVIDIA card is "Not In Use"

---

### Post by hessiess on 2008-04-03
try reatarting x, 

ctrl+alt+backspase

this will shutown any running apps so save first.

you could also check the /etc/X11/xorg.conf file

```
sudo nano /etc/X11/xorg.conf
```

look for a section like this

```

Section "Device"
        Identifier      "nVidia Corporation G70 [GeForce 7600 GS]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection
```

Driver should have "nvidia" after it.

---

### Post by TMcKSmith on 2008-04-03
okay will do, how do I get back to x-server after doing ctrl+alt+backspace

---

### Post by hessiess on 2008-04-03
it dumps you to the log in screen, just log in again ;)

---

### Post by TMcKSmith on 2008-04-03
after installing the glx driver, now my laptop screen is completely blank but the external monitor that I have plugged in is displaying the x-server...but the graphics are god awful

---

### Post by hessiess on 2008-04-03
log in, 

run 

```
sudo nvidia-settings
```

go display config

hit detect displays

select man desplay and activate it, 

change to correct resolution

hit apply

hope it helps

edit;
dose ristricted drivers manager say its using the driver?

---

### Post by TMcKSmith on 2008-04-03
i'm in nvidia=settings and I only have "nvidia-settings Configuration" on the left and checkboxes on the right

---

### Post by hessiess on 2008-04-03
dose it look like this?

[IMG]http://uploader.polorix.net//files/908/images/Screenshot-2.jpg[/IMG]

you may want to check this thred

[http://ubuntuforums.org/showthread.php?t=657141](http://ubuntuforums.org/showthread.php?t=657141)

and

```
sudo nvidia-glx-config enable
```

---

### Post by TMcKSmith on 2008-04-03
no it doesn't look like that at all, it only has the bottom option on the left side

---

### Post by TMcKSmith on 2008-04-03
I also forgot to mention that earlier I installed "Envy" and it successfully (I think) installed the appropriate drivers, and would successfully reboot.  However, when I tried to change the screen settings to dual-screen in KControl it would not reboot successfully.  Perhaps I should let envy install the driver again and go from there?  Afterall, that's further than where I'm at now.

---

### Post by hessiess on 2008-04-03
> **TMcKSmith said:**
> I also forgot to mention that earlier I installed "Envy" and it successfully (I think) installed the appropriate drivers, and would successfully reboot.  However, when I tried to change the screen settings to dual-screen in KControl it would not reboot successfully.  Perhaps I should let envy install the driver again and go from there?  Afterall, that's further than where I'm at now.

give it a go :) you may need to edit etc/X11/xorg.conf manually to get it working.

---

### Post by TMcKSmith on 2008-04-03
Good news (I think) - I ran Envy again, and it said it completed successfully and this time (it didn't last time) it asked me to automatically configure xorg.conf and then asked me to restart.  It restarted fine!  Then I clicked on nvidia-settings (last time when I did this after running Envy it said I was not using the right Nvidia card, driver, or something I can't remember) - but now it looks like the screen shot you posted!  Also, when I go into "Restricted Drivers" it says 'In Use'.  I have no idea why this worked differently this time.  Unfortunately, I'm no longer at my office anymore to test if it works on an external monitor.  I have some old monitors laying around the house, do you think I should test it on that?  Or will that screw things up for the future?  Thanks again for all your help so far, you've been great

---

### Post by hessiess on 2008-04-03
> **TMcKSmith said:**
> Good news (I think) - I ran Envy again, and it said it completed successfully and this time (it didn't last time) it asked me to automatically configure xorg.conf and then asked me to restart.  It restarted fine!  Then I clicked on nvidia-settings (last time when I did this after running Envy it said I was not using the right Nvidia card, driver, or something I can't remember) - but now it looks like the screen shot you posted!  Also, when I go into "Restricted Drivers" it says 'In Use'.  I have no idea why this worked differently this time.  Unfortunately, I'm no longer at my office anymore to test if it works on an external monitor.  I have some old monitors laying around the house, do you think I should test it on that?  Or will that screw things up for the future?  Thanks again for all your help so far, you've been great

glad i was able to help:)
should work the same on any monitor, so long as its not a drastically different resolution. to enable multiple monitors hit the 'detect displays' button in nvidia-settings

---

### Post by TMcKSmith on 2008-04-03
how come the highest resolution I can get for the 2nd monitor is 640x480 (on TwinView)?  Even when I hit "Auto" it defaults to that.  It should be a lot bigger...

---

### Post by hessiess on 2008-04-03
dont know exactily. you may need to add more resolutions to xorg.conf. it dusnt always detect the corect res atomaticly.

---

### Post by TMcKSmith on 2008-04-03
how and where would I add more resolutions to my xorg?  here's what I have right now:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	Defaultdepth	16
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by overdrank on 2008-04-03
> **TMcKSmith said:**
> how and where would I add more resolutions to my xorg?  here's what I have right now:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
[COLOR="Red"]	Defaultdepth	16[/COLOR]
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

Hi and I hate to butt in. The one thing that stands out to me is the default depth is at 16 and usually at 24

---

### Post by TMcKSmith on 2008-04-03
well does that depth apply to the external monitor?  I was under the impression that "screen" section was for my laptop (which is displaying fine)

p.s. thanks for butting in :)

---

### Post by hessiess on 2008-04-03
get both screens working, then hit the save x confing file button, this should add the second screen to the xorg file.

the resolutions are set by the modes keyword

```
Modes "1280x800"
```

just add more to this list

```
Modes "1280x800" "1024x768"
```

etc

---

### Post by TMcKSmith on 2008-04-03
makes sense.  I'll try it out tomorrow at the office.  

okay, so now that I have the NVIDIA graphics card installed...is there anything else I can do with it.  Honestly, everything looks the same as it did before I installed it...is that normal?  Is there anything I should look into as far as graphics go - 3d, this "compiz" I've been hearing about, etc.?  Thanks again!!! much appreciated

---

### Post by hessiess on 2008-04-03
> **TMcKSmith said:**
> makes sense.  I'll try it out tomorrow at the office.  

okay, so now that I have the NVIDIA graphics card installed...is there anything else I can do with it.  Honestly, everything looks the same as it did before I installed it...is that normal?  Is there anything I should look into as far as graphics go - 3d, this "compiz" I've been hearing about, etc.?  Thanks again!!! much appreciated

yep, thats noramal:). if you want to use the graphical effects there under appearance appearances on gnome, don't know where it is on KDE.I cannot offer much advice on compiz because i don't use it:)
Blender works very well on Ubuntu tho.

---

### Post by TMcKSmith on 2008-04-03
Blender looks cool - but that's just a 3d art creation tool right?  I was thinking of something more along the lines of making my desktop look cooler :)

---

### Post by TMcKSmith on 2008-04-04
Hey again -

So I've been playing around with the "NVidia X Server Settings", and I successfully got "Twin View" AND "Seperate X Server" working.  Very cool.  My question is about "Twin View" - is this just supposed to stretch the desktop across two screens?  This is what mine is doing.  Windows still conform to each screen, however I was hoping to get something more like the Seperate X-Windows, but still be able to drag windows across the two screens.  Please let me know if this is possible.

---

### Post by TMcKSmith on 2008-04-07
bump

---

### Post by TMcKSmith on 2008-04-08
sorry to bump again, just wondering if anyone knows the answer to my latest question in this thread.  thanks in advance

---

