---
title: "nvidia and widescreen"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by gp95ac on 2007-09-23
Hi folks,
Im a new user and have found the answers to most of my questions in the forum.  Probably the best part of the ubuntu experience.  So thanks for all the past help!

Here is my issue.  I've got an older dell system (PIII, 933mhz 512mb) with a nvidia geforce2 card (64mb i think) running FF 7.04.  When I enable the restricted drivers, I cannot get 1440x900 widescreen  res.

So I ran sudo dpkg-reconfigure -phigh xserver-xorg and tried to enable that res on the nvidia settings....no dice

Try again with the "nv" drivers and it works perfectly!  

Problem is, there seems to be no 3d acceleration with these, 

gp95ac@Wargnaught:~$ glxinfo
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
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault (core dumped)

so no compiz, desktop effects...heck cant even run glxgears

gp95ac@Wargnaught:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
gp95ac@Wargnaught:~$ 

heres the relavant part of xorg

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


I know it doesnt help alot, with it being generic...my question...is there a way to enable opengl on this driver?  Conversely, could the nvidia driver be tweaked for widescreen?  I think the problem is that the card was created waaay before widescreens came out.  If anyone thinks it will help, I can re-enable the nvidia drivers and repost the glxinfo/xorg.  That said, i would hate to have a widescreen running at less than 1440x900.

Thanks in advance
Cheers
gp

---

### Post by alienexplorers on 2007-09-23
Use the ENVY script to first unload your video drivers and then use it to load your drivers.  After it finishes reboot.  When back up use the command:
> gksudo nvidia-settings
select your video mode and save the settings.

---

### Post by gp95ac on 2007-09-23
I'll give it a go and post back.  So just to clarify, it is possible to get 1440x900 and the opengl running?

Thanks for the speedy reply.

Ill post results tomorrow

gp

---

### Post by gp95ac on 2007-09-23
Alrighty,

Tried it out and it looked as though something was going to happen.  Sadly, no.  

gp95ac@Wargnaught:~$ gksudo nvidia-settings
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

gp95ac@Wargnaught:~$ 


same glxinfo output

and I thought maybe it needs to be enabled via restricted devices...error returned saying my hardware doesnt need restricted drivers.

Any thoughts on the next step?

---

### Post by gp95ac on 2007-09-23
xorg has changed though

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by alienexplorers on 2007-09-23
gksudo nvidia-settings does not still work.  Try reinstalling it. > sudo aptitude reinstall nvidia-settings

---

### Post by gp95ac on 2007-09-23
reinstalled, same error message. 

gp95ac@Wargnaught:~$ sudo aptitude reinstall nvidia-settings
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  nvidia-settings 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/762kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 115508 files and directories currently installed.)
Preparing to replace nvidia-settings 1.0+20060516-3ubuntu1 (using .../nvidia-settings_1.0+20060516-3ubuntu1_i386.deb) ...
Unpacking replacement nvidia-settings ...
Setting up nvidia-settings (1.0+20060516-3ubuntu1) ...

gp95ac@Wargnaught:~$ gksudo nvidia-settings

ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.



 the nvidia gui does fire up, as it did before reinstall, doesnt do anything.  has text on the left, "nvidia-settings configuration", but no amount of clicking or swearing will let me edit config settings

---

### Post by alienexplorers on 2007-09-23
Check out this page:
> [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

and check out this:
> Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

---

### Post by gp95ac on 2007-09-23
How would I verifiy if I've got the right dev tools, headers package, etc?  I'm still a bit green to all of this and the thread has gone from, "ya I'll try that" to "scratches head for an hour" and reposts

---

### Post by gp95ac on 2007-09-23
And I really dont get how the system thinks it doesnt need restricted drivers now.  That nvidia card hasnt just walked off.

Beginning to think its just not gonna happen

---

### Post by gp95ac on 2007-09-23
Would changing Xorg from this....

Section "Device"
Identifier "Generic Video Card"
Driver "nv"
Busid "PCI:1:0:0"
EndSection

to this work?

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
Busid "PCI:1:0:0"
EndSection

Section "Extensions"
**Option "Composite" "1"**
EndSection

---

### Post by gp95ac on 2007-09-23
almost 100 views and only one member has any ideas?

---

