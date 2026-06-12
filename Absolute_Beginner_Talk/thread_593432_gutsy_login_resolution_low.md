---
title: "gutsy login resolution low"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Goupit on 2007-10-27
I use a nvidia card. I used to have the problem with desktop effects. I installed "nvidia-xconfig" and had to automatically remove "nvidia-glx". I run
 sudo nvidia-xconfig --add-argb-glx-visuals -d 24 
as shown in a blog and my effects were ok. After restarting, my login screen was of a much lower resolution than i wanted. And so was my desktop. It seemed that my restricted drivers were deactivated or uninstalled. I re enabled them and run synaptic manager. I saw that a "nvidia-glx new" was now in the list and checked. Now everrything is working well except that my login window resolution is low and what ever changes  i make in System->Administration->Login Window does not take affect. Hope someone has an idea.

---

### Post by benhall on 2007-10-27
Have you tried to use the "Screens and Graphics" dialog? This might be more appropriate for appropriately activating the nvidia as it should (hopefully) add the appropriate x settings for compiz. Also, I assume you are activating desktop effects though the new Visual effects dialog in the "Appearance"?

---

### Post by Goupit on 2007-10-27
Well, ok about desktop effects. I do activate them via the Visual effects dialog in Appearance. Now about the Screens and Graphics dialog. I don't see something about the login window. My resolution is 1280x1024. The resolution i have after i login. The problem exists only when I'm in the login window where i press my user name and password.

---

### Post by sickenmcsluggets on 2007-10-27
I'm having the exact same problem.

---

### Post by TheBigBentley on 2007-10-27
me too.

---

### Post by alfamlap on 2007-10-27
me too with an intel i915. Desktop resolution after login 1280x1024. Login resolution 1280x768.

I have read a lot of threads in different forums about this problem, and nothing, till now, work for me.

Hope somebogy will solve the problem...

---

### Post by Homey on 2007-10-27
I have the same problem..
my laptop works fine with old version 7.04 but with v7.10 i can't get the right resolution plus the right refresh rate .. the only thing to choose is 50 Hz .. it must be 60 Hz 
my video card is nVidia 7300

it is really disappointing :(

---

### Post by drs305 on 2007-10-27
Same problem with me - but only on the initial sign on. Once it booted to the desktop I reset the resolution and it has remained where I put it after the initial change. The initial log-on screen is still very low resolution.

It started happening to me this afternoon when I upgraded my ASUS BIOS.

---

### Post by Papillonrus on 2007-11-22
The answer is here.  I found it once.  You have to create a file to set the login screen resolution.  I'm trying to find it (the answer) again myself.  Post it here if you find it.

---

### Post by doorknob60 on 2007-11-22
> **alfamlap said:**
> me too with an intel i915. Desktop resolution after login 1280x1024. Login resolution 1280x768.

I have read a lot of threads in different forums about this problem, and nothing, till now, work for me.

Hope somebogy will solve the problem...

I'm having the exact same problem (with the same resolutions too) on an intel integrated card ( its the i810 driver i think). I haven't found a fix yet...seems weird but luckily doesn't usually affect it after login.

---

### Post by sickenmcsluggets on 2007-12-26
> **Papillonrus said:**
> The answer is here.  I found it once.  You have to create a file to set the login screen resolution.  I'm trying to find it (the answer) again myself.  Post it here if you find it.
So, uh, did _you_ find it yet?

---

### Post by jas0 on 2007-12-26
I believe you guys may need this:

[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

Hope this helps...

EDIT:
Also, for best results, plug in the model number of your monitor into Google, get the vertical and horizontal refresh rates and plug them into the xorg.conf file (it's all in the post I linked to).

---

### Post by Jallu59 on 2007-12-28
Heimo's advices weren't enough. My xorg.conf is already such. This ugly behavior(1024x768@60Hz) of the login screen came to me along with some update to GutsyBeta, I think it was an update of Xorg, but I'm not sure. In Feisty and in the beginning of using GutsyBeta it was OK. There's something wrong in Gutsy with the harware recognition of my monitor(20-inch tube Eizo Flexscan T662-T) occasionally also, because sometimes the resolution is as awful with every user, normally user desktops are OK(1280x1024@75Hz)

And I have got the T662 configured in xorg.conf.

Yours Jallu59.

---

### Post by easy_target on 2007-12-30
Well, put me on this list as well. No matter how many changes to xorg.conf (Virtual Desktop, removing other resolution modes, using screen and graphics utility), my login resolution is ALWAYS different from my desktop resolution. Is there another file to set resolution for the login screen?
ATI Radeon 9600XT and Westinghouse  L1975NW monitor.

---

### Post by fermin on 2008-01-04
Im having the exact same problem, also resolution after login es 1280x1024, but with very low resolution at login screen. Moreover, the loading bar with the ubuntu logo prior to the login screen doesnt appear anymore. Everything else is normal after session login.

The problem started for me when i tried to use an old nVidia graphics card (TNT2 64) to get the desktop effects to work in my computer. It din't work because the newest nVidia driver required does not support my card anymore; but, in the process, i removed the nVidia drivers, went text only session and restarted my computer according to the instructions on [http://www.compiz.org/NVidia](http://www.compiz.org/NVidia). After realizing it wouldnt work, i changed by to my old SiS graphics card with which all was working fine without "desktop effects" and then the problem started.

Here's my xorg.conf file it is of any help for anyone that knows

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"SiS 300"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	0
	Vendorname	"SiS"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1600x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by fermin on 2008-01-05
> **jas0 said:**
> I believe you guys may need this:

[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

Hope this helps...

EDIT:
Also, for best results, plug in the model number of your monitor into Google, get the vertical and horizontal refresh rates and plug them into the xorg.conf file (it's all in the post I linked to).

The instructions therein did the work for me on this problem; thanks jas0. I just opened the terminal and wrote

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```

and followed the instructions in the xorg configure program that appears; i didn't have to go text mode but still there may be some cases in which this is best. The tricky part is to eliminate the resolutions that you don't want to use from the list when it asks you to in some step of the configuration (you can just put the asterisk with space bar in the only resolution you want to use as i did). Afterwards i restarted my system and my login screen and session had my desired resolution (1280x1024).

Hope this works for more of you. :)

---

### Post by Goupit on 2008-01-19
Followed fermin's tips didn't work for me. All it did was disable my nvidia driver and 3D effects. I activated and all is ok, but nothing has changed to my login window.

---

### Post by easy_target on 2008-01-19
Same here. What is going on?

---

### Post by svartberg on 2008-02-17
Im having the same problem. I installed the ati driver through envy and even compiz is working fine now. But the problem is Im having 800x600 as resolution when I log in to gnome, so I have to manually fix the resolution to 1280x1024. Its a bit annyoing :(

---

### Post by rfurman24 on 2008-02-17
Installing startup-manager in synaptic will let you adjust the boot and gdm screen resolutions.

---

### Post by RedBird on 2008-02-22
Still I have the same problem with my login screen.

I just want to know where exactly are the settings of the login screen stored.. not the [COLOR="Red"]**splash screen**[/COLOR] nor the [COLOR="Red"]**desktop screen**[/COLOR].. just the [COLOR="Red"]**login screen**[/COLOR]!! and I mean by the login screen is the screen where you put your login name and password..

---

### Post by philinux on 2008-02-22
As has been mentioned startupmanager can fix this issue. It added vga=792, to the kernel line in grub, in my case for a res of 1024x768. You can do that yourself by editing /boot/grub/menu.lst

---

### Post by ubunteira on 2008-02-24
Seems that I am member of the same club "RongLoginResolution Club"
My card is nvidia Geforce2 ti. Distr 7.10. Desktop resolution 1280x768. Login resolution somewhat 1024x 900? I'm not sure. I wondering which file determinate login resolution?

---

### Post by n-alexander on 2008-02-25
> **philinux said:**
> As has been mentioned startupmanager can fix this issue. It added vga=792, to the kernel line in grub, in my case for a res of 1024x768. You can do that yourself by editing /boot/grub/menu.lst

I already have vga=792 there. Seems it refers to another resolution in my case. I need 1024x768, but get something much higher. Where are these modes/IDs defined?

---

### Post by n-alexander on 2008-02-25
> **n-alexander said:**
> I already have vga=792 there. Seems it refers to another resolution in my case. I need 1024x768, but get something much higher. Where are these modes/IDs defined?

Disregard, I've just been slow. This does fix the issue, thanks!

---

