---
title: "Enabling Direct Rendering, Nvidia Drivers Installed"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Orkin on 2007-05-04
Basically I need to enable OpenGL and Direct Rendering, they dont seem to be on at current, even though my card (nvidia GeForce Fx5200) does support it and the drivers are fully installed and updated. 

Heres my xorg.conf:

```

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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"uk"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"HWP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"HWP"
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
```

So how do I go about doing this?

---

### Post by justleen on 2007-05-04
what does ```
glxinfo |grep version
``` tell you?

your xorg is fine...

---

### Post by Orkin on 2007-05-04
```
owen@owen-desktop:~$ glxinfo |grep version
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 1.2 (2.0.2 NVIDIA 87.76)

```

?

---

### Post by viciouslime on 2007-05-04
> **Orkin said:**
> ```
owen@owen-desktop:~$ glxinfo |grep version
server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL version string: 1.2 (2.0.2 NVIDIA 87.76)

```

?

You're using an old nvidia driver, are you using the one from the repos? Are you using edgy rather than feisty?

---

### Post by Orkin on 2007-05-04
Im using Dapper. So do I have to upgrade to use OpenGL then? :(

---

### Post by alienexplorers on 2007-05-04
I have the same graphics card as you.  My output of glxinfo is as follows:

> terminator@terminator-desktop:~$ glxinfo |grep version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.0 NVIDIA 97.46
glu version: 1.3
terminator@terminator-desktop:~$


My drivers were loaded by using the ENVY script in Dapper.

---

### Post by viciouslime on 2007-05-04
> **Orkin said:**
> Im using Dapper. So do I have to upgrade to use OpenGL then? :(

No, but to use direct rendering you do... well you need to upgrade your nvidia driver at least. I would recommend upgrading to feisty, dapper is very dated now. However, if you would rather stick with dapper for whatever reason, you could install an updated nvidia driver either directly from nvidias site following their instructions, or, using the ENVY script, see here: [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

Hope that's some use to you :)

---

### Post by viciouslime on 2007-05-04
Oh, just found this on the website above: > The support for Dapper has been temporarily removed in series 0.9.x (See my Blog  for an explanation of Envy's features)

Looks like you might have to go it alone with the nvidia site, or, upgrade to feisty.

---

### Post by Orkin on 2007-05-04
> Please select one of the activities displayed above and press ENTER:

1
ENVY ERROR: Your Operative System does not seem to be supported by Envy


>_<

Meanwhile Im being told:

> owen@owen-desktop:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.


>__>

Thanks for the help anyway, I think I'll just upgrade to 7.04.

---

### Post by viciouslime on 2007-05-04
Yeh, if you see my post above you'll see I just noticed that dapper is no longer supported by edgy, sorry. But it is well worth the upgrade anyway :)

---

### Post by Bachstelze on 2007-05-04
First off, remove "	Load	"dri"", it shouldn't be there. Then, if it still doesn't work, try upgrading your driver s with the installer from nvidia's website, it is pretty straightforward :

```

apt-get remove nvidia-glx* linux-restricted-modules*
apt-get install build-essential linux-headers-$(uname -r) pkg-config xorg-dev
```

and off you go :p

---

### Post by alienexplorers on 2007-05-04
"ENVY" can still be used with Dapper if you use version 0.8.2.  I have used it several days ago and it works perfectly.

---

### Post by lakersforce on 2007-05-04
If you scroll down long enough you will find an envy script that is working for Dapper. I would recommend using this. And it is absolute nonsense that there is no support and no 3d accel. in Dapper. DIRECT RENDERING WORKS ABSOLUTELY FINE IN DAPPER! I see you have already installed the driver, now you just need to enable them. If you for some reason will not use the envy script, which I recommend you to do, this is the way to proceed:

First back-up your xorg.conf file in case you display gets screwed up:

```
sudo cp /etc/X11/xorg.conf /etx/X11/xorg.conf.backup
```

Now you can just replace to xorg.conf with the back-up file, in case that after doing the following you will be greeted by linux by the "Blue-Screen-of-Death". The next couple of lines might or might not work when logged into the desktop. If it does not work, you should stop the graphical display manager.

But to enable:

```
sudo nvidia-glx-config enable
```

```
sudo dpkg-reconfigure xserver-xorg
```

and here you should choose "nvidia".

To switch console press ctrl+ alt +f1-8 or just alt + f1-8. The graphical console, when enabled is always on console 7. To stop the graphical manager:

```
sudo /etc/init.d/gdm stop
```
If you are using KDE the command would be kdm, instead of gdm. Start or restart restarts the graphical manager.


On a sidenote, if you want to upgrade you installation I would recommend Ubuntu 6.10 Seems like it is the most stable and bug-free version. Sorry to all the fan-boys and girls out there, but Canonical did not do a very good job on Feisty Fawn.

---

