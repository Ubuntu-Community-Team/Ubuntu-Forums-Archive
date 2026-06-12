---
title: "nvidia driver, wrong output from glxinfo?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Sceiron on 2008-02-15
Hey,
two days ago i messed up my xorg.conf, so i ran the command:
 sudo dpkg-reconfigure -phigh xserver-xorg

After that i had some trouble with X since it was complaining about the driver was not present...
 so i've just installed the latest nvidia driver through the Restricted driver manager, and it seems to be working, but when i type 'glxinfo' in terminal it returns:

@gutsy:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


I suspect there are some issued here, i was expecting to get the driver version, and instead i got a lot of text i dont understand anything about...
Can someone explain to me what the error is, not just provide the solution, so i can learn something (i hope) from it :)

Thanks!

---

### Post by ashmew2 on 2008-02-15
How can you reach "it seems to be working" ? Is the nvidia logo showing up when you boot up your system ?

---

### Post by Sceiron on 2008-02-15
> **ashmew2 said:**
> How can you reach "it seems to be working" ? Is the nvidia logo showing up when you boot up your system ?

Well, the logo is not showing up.
But before i installed the driver i had to run in "safe grafics mode". When i restarted after installing the driver it started in "normal" mode if u like... So now i have my screens native resolution.

edit:
here's the output of my xorg.conf:
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
	Identifier	"nVidia Corporation G80 [Quadro NVS 140M]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [Quadro NVS 140M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"
	EndSubSection
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
Section "Module"
	Load		"glx"
EndSection

edit 2:
Do i have to define the driver under the screen section?

---

### Post by ashmew2 on 2008-02-15
Well it says there Driver "nvidia" 

How about running nvidia-xconfig ?
back up your xorg before that , it might screw up your system. So you can always restore the backup.

---

### Post by Sceiron on 2008-02-15
It gave the same result as the first post..
edit:
by that i mean i tried your suggestion.

---

### Post by ashmew2 on 2008-02-15
OK , have you given Envy a try ? [www.albertomilone.com](www.albertomilone.com)

First Uninstall the Nvidia Driver then reboot and install the Nvidia Driver (use envy for install/uninstall) 
Post the output of glxinfo then.

---

### Post by TheBoat on 2008-02-16
I also recommend using Envy.  It fixed my NVIDIA driver, and it will automatically remove your old driver.  Envy was created by a moderator here at Ubuntu Forums.

---

### Post by Sceiron on 2008-02-16
When i try to run envy i get the following output from terminal:

(Reading database ... 137035 files and directories currently installed.)
Preparing to replace envy 0.9.10-0ubuntu2 (using envy_0.9.10-0ubuntu2_all.deb) ...
Unpacking replacement envy ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

Seems like im missing some dependencies, but how do i get them?

But on the other hand i feel like its not the driver itself that is the problem, but rather the interface with the driver....just thinking out load.

Anyone have any ideas or solutions ?
I dont like to say it, but im on the brink of reinstalling ubuntu...

---

### Post by TheBoat on 2008-02-16
This might repair the problem:```
sudo get-apt install -f
```Otherwise, just open up Synaptic and install the packages it asks for yourself.

---

### Post by ashmew2 on 2008-02-17
```
sudo apt-get install xserver-xorg-dev module-assistant fakeroot dh-make debhelper dpatch build-essential
```

Give that a try and then try installing Envy.

---

### Post by Sceiron on 2008-02-17
> **TheBoat said:**
> This might repair the problem:```
sudo get-apt install -f
```Otherwise, just open up Synaptic and install the packages it asks for yourself.

I tried this, and the packages was installed.
So i set of installing envy. But when installing envy iti gave a small error-msg. But the installation was fullfilled apperantly. 
Then i tried to install the nvidia driver throug the Applications->systemtools->Envy.

Then reboot, and the result was:
1. Starting up in safe grafics mode.
2. glxinfo still doesnt work
3. if i look under RDM it has no driver enabled (dont know if that matters with envy)

Same output from glxinfo....

But on the other hand:
Do i really need glx?
From my limited knowledge i know that glx maintains the interface between OpenGL and X11.
So when i install the latest nvididriver which seems to be working, does the nvidia driver handle this protocol??
Anyone has any ideas about this?
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+question/13293](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-via/+question/13293)

Thanks for all help so far guys.
Best regards 
Sceiron

---

### Post by ashmew2 on 2008-02-17
You mean you want to install the newest Nvidia driver they are giving on their site ?

[www.nvidia.com](www.nvidia.com) ?

That is definitely worth a try. I think Envy does the same for you though.

---

### Post by erginemr on 2008-02-17
If you are planing to use Compiz and play 3-D games, then you need to have "glx" enabled.

1. In your previous xorg.conf file, there was a line:
```
Modes "1440x1440"
```
which means your screen should be running at 1440x1400. However, your natural resolution is 1440x900.

2. Can you please post your latest xorg.conf file?

3. +1 to **ashmew2**. AFAIK, Envy fetches the correct driver from NVIDIA web site.

4. Envy should have uninstalled "nvidia-glx-*" from your system first before installing the one from NVidia web site. Can you please check from Synaptic that it is not installed?

5. "What did i do to xorg.conf this time....." (your signature) :lolflag:

---

### Post by Sceiron on 2008-02-17
> **ashmew2 said:**
> You mean you want to install the newest Nvidia driver they are giving on their site ?

[www.nvidia.com](www.nvidia.com) ?

That is definitely worth a try. I think Envy does the same for you though.

Yupp, did that with the following result:
- The driver seems to be working.
- glxinfo doesnt work. (or glx is not present in my system)
I dont understand much of this....

Edit:
When i tried doing this with/through envy, as posted in the previous post, the driver doesnt work.
I'll fetch my xorg.conf again.

---

### Post by Sceiron on 2008-02-17
> **erginemr said:**
> If you are planing to use Compiz and play 3-D games, then you need to have "glx" enabled.

1. In your previous xorg.conf file, there was a line:
```
Modes "1440x1440"
```
which means your screen should be running at 1440x1400. However, your natural resolution is 1440x900.

2. Can you please post your latest xorg.conf file?

3. +1 to **ashmew2**. AFAIK, Envy fetches the correct driver from NVIDIA web site.

4. Envy should have uninstalled "nvidia-glx-*" from your system first before installing the one from NVidia web site. Can you please check from Synaptic that it is not installed?

5. "What did i do to xorg.conf this time....." (your signature) :lolflag:

Xorg.conf:
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

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

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "Screen0" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	28.0	-	72.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"LEN"
	Horizsync	46.3	-	55.7
	Vertrefresh	50.0	-	60.0
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [Quadro NVS 140M]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"Quadro NVS 140M"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [Quadro NVS 140M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"nvidia-auto-select +0+0"
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


Now i kinda think that if i disable "Composite" in endsection it maybe can fix the problem.
Cause in the first post it seems that there is a problem with the RGB interface or something, but i thought that RGB had to do with Component-interface, not Composite-interface....
hum ?

---

### Post by Sceiron on 2008-02-17
> **erginemr said:**
> 

4. Envy should have uninstalled "nvidia-glx-*" from your system first before installing the one from NVidia web site. Can you please check from Synaptic that it is not installed?


How do i do this ??

Best regards :)

---

### Post by ashmew2 on 2008-02-17
He meant that Envy removes all the previous Nvidia Driver packages you have and installs the newest available one.
To be safe ,when you start Envy , First thing you should do is "Remove Nvidia Driver"
Then you reboot and do a "Install NVIDIA Driver" by using Envy.

---

### Post by Sceiron on 2008-02-17
I have tried that, without sucess...

---

### Post by Sceiron on 2008-02-17
Is it possible to reinstall/repair ubuntu without loosing personal data?
This problem is beyond my skills to fix...

---

### Post by erginemr on 2008-02-17
None that I know. You will have to start over. 

But you can save the contents of your "/home/your_name" folder and "/etc" folder (these two hold most of your customized settings) to say, a pen drive for later reference or partial restore.

I am so sorry that your problem could not be resolved...

---

### Post by erginemr on 2008-02-17
I went to [www.nvidia.com](www.nvidia.com). Yet under the section: support -> drivers -> linux drivers, there is seemingly no "nvidia nvs 140m" although there are similar model names. Alas, as a GeForce 4 MX user, this model is just too strange to me.

Only if you could find out the correct driver and download the corresponding "*.run" package, I would try to guide you further through the installation. But it is your call, of course.

---

### Post by Sceiron on 2008-02-17
Thanks for the answer. 
I have tried installing the driver manually from nvidia.com, and automatically through envy. And that would be the latest driver for nvidia for both attempts.
The driver has worked before, but i tried to install the settings manager for compiz, and one failed attempt to create a conky... Think somewhere along the way i screwed up real bad...
I have been googling/reading about the same problem with glxinfo for others, but what has worked for them, doesnt work for me....

I think i will format and reinstall after i get my hands on a external Harddrive.
Thanks anyways.
Sceiron.

---

### Post by ashmew2 on 2008-02-18
Well its just too bad your problem cant be resolved...I hope someone replies soon enough , or at least enlightens us about how to fix if we encounter something similar..

---

### Post by Sceiron on 2008-02-18
Is there someone who knows exactly what the problem is?
I'll keep this thread open until i get a storagemedium...

---

### Post by Sceiron on 2008-02-18
[http://forum.freespire.org/showthread.php?t=10435&highlight=Xlib%3A+extension](http://forum.freespire.org/showthread.php?t=10435&highlight=Xlib%3A+extension)

I have also tried this solution, but when it came to this part:
aticonfig --overlay-type=Xv

it would not recognice the command, is this not compatible with Ubuntu?

---

### Post by Sceiron on 2008-02-18
[http://www.opencascade.org/org/forum/thread_12894/](http://www.opencascade.org/org/forum/thread_12894/)

> Do you have the correct opengl hardware drivers installed (if you have 3d graphics card) or the Mesa opengl libraries (atleast for software emulation) installed?

How do i check what Mesa opengl libraries is installed?
And what version should be the correct one ?:confused:

---

### Post by Sceiron on 2008-02-19
-bump-
Is about time for a serious bump on this thread...

---

### Post by erginemr on 2008-02-19
I am eavesdropping your posts my friend, but do not interfere since I am at the end of my wits. However, maybe a slight hope: 

Assuming you have installed the binary driver from Envy or directly from NVidia web site, and that you have removed whatever nvidia-* from Synaptic, I remember there was a file somewhere under "/etc" that enables/disables modules to seek at startup. I will look for the file name but the module to disable is "nv", so that the one in your "restricted-modules" will not interfere with the one that you have built for your kernel when you installed the NVidia-* run package.

Did you try this?

---

### Post by erginemr on 2008-02-19
The file in question is:
/etc/default/linux-restricted-modules-common 

You should change the last line as:
DISABLED_MODULES="nv"

and restart. Chance of success is very low, but I hope that I am wrong.

---

### Post by Sceiron on 2008-02-19
> **erginemr said:**
> The file in question is:
/etc/default/linux-restricted-modules-common 

You should change the last line as:
DISABLED_MODULES="nv"

and restart. Chance of success is very low, but I hope that I am wrong.

Now it is stating:
DISABLED_MODULES="nv nvidia_new"

so ill try change it as you have proposed.

edit:
It didnt give any reult, still in safe grfcs mode..

---

