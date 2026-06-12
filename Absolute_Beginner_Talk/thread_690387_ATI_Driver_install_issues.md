---
title: "ATI Driver install issues"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by SteveOSupremo on 2008-02-07
Ok so I just set up a new computer and was tired of Windows.  so I decided to install Ubuntu which brings me to my questions.

1)  How do I know if I have the latest drivers for my devices?  ie Video, Sound, Network, etc.

While trying to follow the Ubuntu WAY guide at the [ATI driver wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") i ran into some problems with the ```
sudo gedit /etc/X11/xorg.conf
``` command.  it tells me something like the file was not found please copy it there.  I looked in the /etc/X11/ folder for the file and all I found was xorg.conf.original.o (or some thing like that)

after that way failed i tried downloading the package from ATI and tried to follow their install method.  and since I'm new at this I have no idea how to run the .run package.

I also noticed that in the install instructions on the ATI AMD site that it states that you need to have 

> Minimum System Requirements

Before attempting to install the ATI Proprietary Linux Graphics Driver, the following software must be installed:

    * POSIX Shared Memory (/dev/shm) support is required for 3D apps
    * glibc version 2.2 or 2.3
    * Linux kernel 2.6 or higher
    * XOrg 6.7, 6.8, 6.9, 7.0, 7.1, 7.2 or 7.3.

	Note: 	If a Linux 2.6.11 or newer kernel was built with CONFIG_AGP enabled, the kernel AGP frontend is required to load the fglrx kernel module. To identify whether your kernel was built with CONFIG_AGP enabled, look for CONFIG_AGP=y in the kernel config file, or if the 'agpgart' module loaded.
System Recommendations

For best performance and ease of use, AMD recommends the following:

    * Kernel module build environment - should include the following:
          o Kernel source code: Either the Kernel Source or Kernel Headers packages 
    * ISSE Support enabled in your Linux Kernel
          o Applies to Intel Pentium III and later CPUs only
          o Enabled by default on version 2.4 and later kernels 
    * The rpm utility should be installed and configured correctly on your system, if you intend to install via RPM packages 

The following packages must be installed in order for the Catalyst™ Linux driver to install and work properly:

    * XFree86-Mesa-libGL
    * libstdc++
    * libgcc
    * XFree86-libs
    * fontconfig
    * freetype
    * zlib
    * gcc 

2) how do I find out if I have all these things installed?  or how do I install them?

3) should I try the manual way?  with the new Catalyst 8.01 driver file?

**System Specs:**
AMD Phenom™ 9500 quad core
Video card: Gigabyte GV-RX385256H (ATI HD3850 chipset)
Motherboard: Gigabyte GA-MA770-DS3
4 x1 gig DDR2 800

Thanks
SteveO

---

### Post by obscur156 on 2008-02-07
An easy way for installing ATI driver is ENVY.
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

Hope this will help and welcome to Ubuntu and have fun with your new distro.
Regards

---

### Post by SteveOSupremo on 2008-02-07
> **obscur156 said:**
> An easy way for installing ATI driver is ENVY.
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

Hope this will help and welcome to Ubuntu and have fun with your new distro.
Regards

Will Envy take care of any dependencies that I may have / need?

thanks

---

### Post by obscur156 on 2008-02-07
Yes my friend,you select automatic install and voila.

---

### Post by SteveOSupremo on 2008-02-07
Ok I must be an utter newb here!  I can't even get that to work. 

The last thing that I see is the ATI Tech Generating package....

it goes through a couple other lines and comes to a prompt where it asks if I want to auto configure my xorg.conf and I say yes.  and then nothing.  I reboot and am at the same place I was when I started.

BTW i can't find the xorg.conf file. there is an xorg.conf.original-0 file in the /etc/X11 directory is that the file that is supposed to be edited?


any suggestions?

thanks
SteveO

---

### Post by Shadowmeph on 2008-02-08
> **SteveOSupremo said:**
> Ok I must be an utter newb here!  I can't even get that to work. 

The last thing that I see is the ATI Tech Generating package....

it goes through a couple other lines and comes to a prompt where it asks if I want to auto configure my xorg.conf and I say yes.  and then nothing.  I reboot and am at the same place I was when I started.

BTW i can't find the xorg.conf file. there is an xorg.conf.original-0 file in the /etc/X11 directory is that the file that is supposed to be edited?


any suggestions?

thanks
SteveO

I am not sure if this is answered yet but after you get Envy installed you have to start up Envy which is ( on my comp) listed under applications ( I think I am in windows right now ) then system it should say Envy in there

---

### Post by dalvon on 2008-02-09
Okay I have my ATI video drivers installed now correctly I used Envy, but my fps is extremely low especially for my card. I have a Sapphire X1950 PRO 256 MB PCI Express.

When I run glxgears I get this:

> 300 frames in 5.0 seconds = 59.984 FPS
303 frames in 5.0 seconds = 60.060 FPS
303 frames in 5.0 seconds = 60.014 FPS
288 frames in 5.0 seconds = 57.529 FPS
292 frames in 5.0 seconds = 58.318 FPS
300 frames in 5.0 seconds = 59.423 FPS
304 frames in 5.0 seconds = 60.199 FPS
285 frames in 5.0 seconds = 56.463 FPS
263 frames in 5.0 seconds = 52.600 FPS
275 frames in 5.0 seconds = 54.668 FPS
301 frames in 5.0 seconds = 59.998 FPS
285 frames in 5.0 seconds = 56.851 FPS
277 frames in 5.0 seconds = 55.010 FPS
301 frames in 5.0 seconds = 60.042 FPS
301 frames in 5.0 seconds = 59.776 FPS
271 frames in 5.0 seconds = 54.029 FPS
303 frames in 5.1 seconds = 59.887 FPS
302 frames in 5.0 seconds = 59.960 FPS
X connection to :0.0 broken (explicit kill or server shutdown).


Which is strange because my card works perfectly in Windows XP Pro 64-bit

[HTML]# xorg.conf (xorg X Window System server configuration file)
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
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
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

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Sceptre"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "XaaNoOffscreenPixmaps"
	Option	    "UseFastTLS" "2"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Sceptre"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1680x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection[/HTML]

Compiz is working 
Beryl is working

Just my frame rates are really really really slow.

---

### Post by dalvon on 2008-02-09
I figured out what the problem was and it was something I changed in the ATI Catalyst Control Center. I had set the Wait for Vertical refresh to the highest settings which lowered my fps to almost nothing.

---

### Post by SteveOSupremo on 2008-02-11
ok so I finally got it working after I re-installed Ubuntu.

I then was able to find the xorg.conf file and was able to edit it.  

anyway.  the next problem was that I couldn't get the big monitor to work whenever I would change it to that the resolution would go wierd and I could never get it to do a 1280 by1024 on each monitor. and when I would get it close and restart the settings would revert to some previous state.  anyway I needed a computer up and running so I went back to windows XP and spent the next 3 days installing updates and patches and updates to the patches.  ugggg.

anyway maby with the next release I'll try again.  hopefully by that time ATI cards and games are better supported.

I am trying out a Mythbuntu install now on another computer we'll see if that can restore my faith and get me primed for a full Ubuntu install.

SteveO

---

