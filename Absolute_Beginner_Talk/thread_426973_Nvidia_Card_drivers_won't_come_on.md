---
title: "Nvidia Card drivers won't come on"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by philby on 2007-04-29
I know it sounds weird but regardless on how may time I click on the select the  restricted driver for the Nvidia card it won't accept it. I select it click enable and no change is seen, tried to reboot just in case it had been selected but still no go???

Any ideas??? - Thanks Phil

---

### Post by Kobalt on 2007-04-29
What is the exacy model of your nvidia card ? 
Have you search for and installed manually either nvidia-glx-new, nvidia-glx or nvidia-glx-legacy (depending on your graphic card) from Synaptic ?
If it's not installed then do it and then run ```
sudo nvidia-xconfig
```
Reboot and you should be done.

---

### Post by Cariboo1938 on 2007-04-29
Hi,
I have a similar problem ... after upgade to Feisty I lost my GUI. I had to use driver 'NV" to get GUI back. 
I found in /etc/X11/xorg.conf > Section "Device"
    Identifier     [COLOR="Magenta"]**"NVIDIA Corporation NV34 [GeForce FX 5200]"**[/COLOR]
    Driver         "nv"
EndSection
How can I determine which of the nVidia drivers> either nvidia-glx-new, nvidia-glx or nvidia-glx-legacy 
I need to install? for this card????
....Thanks
Cariboo

---

### Post by Kobalt on 2007-04-29
According to the [nvidia website]("http://www.nvidia.com/object/IO_18897.html") your card is meant to use the 9755 drivers, that is to say the nvidia-glx-new package.

---

### Post by orb9220 on 2007-04-29
Yep that is for my FX5200 nvidia-glx-new. Here is my xorg for beryl and dual crt's.
> 
Section "Monitor"
	Identifier	"A75f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A75f"
	DefaultDepth	24
        Option	       "AddARGBVisuals"	   "True"
        Option         "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

---

### Post by Cariboo1938 on 2007-04-29
> **Kobalt said:**
> According to the [nvidia website]("http://www.nvidia.com/object/IO_18897.html") your card is meant to use the 9755 drivers, that is to say the nvidia-glx-new package.Thanks, Kobalt,
when I install this nvidia-glx-new package via Synaptic, after restart my GUI is killed. I have to edit /etc/X11/xorg.conf and set the driver to "nv" again. Do you have an idea what could be wrong here?

---

### Post by Cariboo1938 on 2007-04-29
> **orb9220 said:**
> Yep that is for my FX5200 nvidia-glx-new. Here is my xorg for beryl and dual crt's. 
Thanks, orb, I wonder don't you have a Section "Device"? Mine looks like this: > Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nv"
EndSection
If the driver is not "nv" my GUI wont work! 
What's wrong?

---

### Post by orb9220 on 2007-04-29
Sorry incomplete
> 

Section "Monitor"
    Identifier     "A75f"
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"TwinView" "on"
        Option          "NvAGP" "3"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "30-70"
	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" "RightOf"		
	Option		"ConnectedMonitor" "CRT,CRT"
	Option 		"AllowGLXWithComposite" "true"
	Option		"RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"A75f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"A75f"
	DefaultDepth	24
        Option	       "AddARGBVisuals"	   "True"
        Option         "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

---

### Post by Cariboo1938 on 2007-04-29
> **orb9220 said:**
> Sorry incompleteLooks good, how did you get this running? Did you do a new Install or an upgrade from the Internet? How did you set all these options in the Section "Device"? Does this come with "nvidia-glx-new"?

---

### Post by medya on 2007-04-29
whats your card ? have you[ tried this ? ]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html")

---

### Post by Cariboo1938 on 2007-04-29
> **medya said:**
> whats your card ? have you[ tried this ? ]("http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html")My Card is "NVIDIA Corporation NV34 [GeForce FX 5200]". I tried several things, but not exactly yours...as soon as my driver in xorg.conf is different from "nv" my GUI dies. Maybe it has something to do with this new kernel - 2.6.20-15-generic x86_64 GNU/Linux-?

---

### Post by orb9220 on 2007-04-29
Just used envy script. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Cariboo1938 on 2007-04-29
> **orb9220 said:**
> Just used envy script. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)I know...I tried this already and here comes what I got: a message that there was an error in the installation process. 
You can see the log file /var/log/envy-installer.log:

> vi /var/log/envy-installer.log
python pulse.py nvidia
root@BitByters-Desktop:/usr/share/envy# python pulse.py nvidia
ENVY ERROR: [COLOR="Red"]**Your Operative System does not seem to be supported by Envy**[/COLOR]
Strange, isn't it? Do you have an idea what that means? 
I have kernel 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux running.update.

Update May 01, 2007:
I contacted Alberto (Envy) and he recommended to install the newest, unstable version of envy. I did this and there was no error during installation...but the result was as before: After restart my GUI didn't start. So my guess is that the online upgrade to Feisty is screwed up. I close this case until I did a new installation from a shipped CD. 
Thanks to all for helping in this case..
Cariboo:guitar:

---

### Post by philby on 2007-04-30
Well I fixed the problem simply by updating using the synaptic manager and vioa restriced driver downloaded and installed fine.

FYI - Running on a Dell 9400 with a 7900Go Nvidia card - also managed to get Beryl running using again the synaptic manager and have emerald as the theme, not to sure what I'm doing yet but I must say I'm rather impressed with this OS - so far no crashes and everything seems to work even the SD card slot works like a charm, bloody hell even Vista RC2 had problems with this.

Still I trying to figure out how to rotate the 3D cubes and install an update to the openoffice, downloaded the latest update for Linux and can't figure out how to install it. I know it's teething problems but when your used to running an .exe file (after scanning it for virus files of course) its had to come to grips with a new way.

---

