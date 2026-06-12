---
title: "Setting up NVidia card"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by swey on 2007-03-31
Hi yes I'm new to this. Just installed edgy 6.10 Ubuntu last night though I've been experimenting with various Live CD's for a while.

Everything went smoothly except I can't seem to get the display to run at anything over 1024 @ 60 refresh rate or to anti alias fonts etc. I have an old but fairly decent card - it's an NVidia GeForce 2 Ultra.

I thought I had done my research - I installed the restricted libs from Synaptic as recommended in the user guide and went to this page:

[https://launchpad.net/ubuntu/edgy/i386/nvidia-glx-legacy/1.0.7184+2.6.17.5-11](https://launchpad.net/ubuntu/edgy/i386/nvidia-glx-legacy/1.0.7184+2.6.17.5-11)

to dl and install the legacy drivers (they weren't in Synaptic) and ran the command prompt recommended. While Console didn't tell me I had run an incorrect command or anything nothing has changed in my system - I have rebooted but still can't access any sort of settings utility to use graphics hardware acceleration and my screen res remains poor. What else do I need to do?

thanks

ps - also I can only seem to network one way - I can browse other computers on my home network but they can't seem to browse (or even see) my Ubuntu PC. I presume I need to make it a server somewhere but how?

---

### Post by peebly on 2007-03-31
Have you tried using envy to install the nvidia drivers.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Dayylin on 2007-03-31
I would follow peebly's advice. Envy makes installing the new drivers a breeze.  Once you use Envy, to access the settings, it will be under Applications>System tools. Or atleast it is on my system running Ubuntu 6.10

---

### Post by swey on 2007-03-31
Thanks. I ran Envy and it did it's stuff - I now have an NVidia settings applet under System tools but there is nothing that lets me enable hardware acceleration and the display res is still stuck under 1024 @60 refresh.

I tried the Console command again (from the above page) but this time I got an error message:

"Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."

What else do I need to do?

---

### Post by jem7v on 2007-03-31
Have you changed your driver from nv to nvidia in your xorg.conf yet?  If not:

```
sudo nano /etc/X11/xorg.conf
```

Scroll down to where it says "Section "Device"" and make sure Driver says "nvidia" instead of "nv" then exit and save (Ctrl+X, Y for yes, Enter).  Then log out, press Ctrl+Alt+Backspace to restart your X server, and see what happens.

If all hell breaks loose and things don't work, switch into a different console (i.e., Ctrl+Alt+F1), log in, go back into your xorg.conf file and change it back to nv, and then use the following code to restart the X server again if Ctrl+Alt+Backspace doesn't do anything:

```
sudo /etc/init.d/gdm restart
```

---

### Post by swey on 2007-03-31
This is what the Xorg file says:

Section "Device"
	Identifier	"NVIDIA GeForce2 Ultra"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce2 Ultra"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

can I just add extra modes using a text editor and resave or is it more difficult?

---

### Post by swey on 2007-03-31
Some one on another forum has shown me how to setup XORG using:

```
sudo dpkg-reconfigure xserver-xorg 
```

bit complicated but I've got a high res at least. However I think there's something wrong with the way it's handling Open GL as non of the GL based screensavers will run and displays are a bit sluggish. How can I setup proper graphics acceleration?

Also I've managed to set up a shared folder and installed Samba to do this but it still doesn't show on other computers (running Windows XP). On Knoppix, which I have also tried, there was a simple icon you clicked on to start Samba server and then all you did was enter your name and password but I can't see an equivalent on Ubuntu.

---

### Post by peebly on 2007-03-31
> **swey said:**
> Some one on another forum has shown me how to setup XORG using:

```
sudo dpkg-reconfigure xserver-xorg 
```

**bit complicated but I've got a high res at least. However I think there's something wrong with the way it's handling Open GL as non of the GL based screensavers will run and displays are a bit sluggish. How can I setup proper graphics acceleration?**

Also I've managed to set up a shared folder and installed Samba to do this but it still doesn't show on other computers (running Windows XP). On Knoppix, which I have also tried, there was a simple icon you clicked on to start Samba server and then all you did was enter your name and password but I can't see an equivalent on Ubuntu.

Did you try setting the res using the nvidia control panel, then click *save to x configuration file*, rather than using the terminal.

I am sure envy enables  graphics acceleration, maybe its just your card, some of the screen savers are quite demanding.

---

### Post by swey on 2007-03-31
They worked fine when I was running it from the Live Cd and that was without the NVidia drivers. The NVidia setup panel doesn't seem to have anything for resolution settings  - just stuff like Antialiasing and colour control.

---

### Post by jem7v on 2007-04-01
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) talks about broken resolutions.

---

### Post by swey on 2007-04-01
Thanks - that sudo reconfig xorg command is what I did - I've fixed the resolution problem but its not using Open GL as far as I can see and isn't fully using hardware acceleration. In Windows its a simple slider in the display settings - why does it have to be so complicated?

---

### Post by jem7v on 2007-04-01
...because your card was built by NVidia with Windows in mind, and official Linux support was a much later afterthought?

---

### Post by swey on 2007-04-14
> **jem7v said:**
> ...because your card was built by NVidia with Windows in mind, and official Linux support was a much later afterthought?

I thought you must be right at first....but this is strange as I've just tried a Live Cd of Xubuntu 6.10 and straight "out of the box" it's giving me the full range of resolutions for my card/monitor (up to 1900) and OpenGL screensavers are all working with that so there must be more I can do to improve graphics performance in Ubuntu?

---

### Post by forrestcupp on 2007-04-14
If you reconfigured your xserver, you may be back to the nv drivers instead of nvidia.  The opensource nv drivers don't support opengl.  Try editing the xorg.conf file just to make sure that under the Device section, the Driver is "nvidia" and not "nv"  If you can't get a higher resolution with nvidia drivers even with the settings manager, try adding the resolution you want to the Modes line under Depth 24.  Remember that the first resolution listed on that line is what it will automatically boot to.  So if you add something there and it messes up, you may have to change it back.

---

### Post by swey on 2007-04-14
No it's def the NVidia drivers - I've copied the whole conf file here to see if anyone can see what I've done wrong because to me it looks like it should. I have the res I want (1024x768 at 85 is fine for me) but it's just not giving me accelerated 3D graphics now and several apps that seem to need hardware acceleration just crash on startup (e.g. AWN and a Planetarium app I wanted to try) and 3D screensavers just don't run at all.

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
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"NVIDIA Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Iiyama MA203DT"
	Option		"DPMS"
	HorizSync	28-85
	VertRefresh	43-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
	Monitor		"Iiyama MA203DT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

I know it's not the card as it runs fine in Xubuntu (and windows)

---

