---
title: "External Monitor Problems in Gutsy"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by HDave on 2007-11-04
Hi,

I am brand new to Ubuntu and to Linux.  I'm giving it a try because I love the idea of an open source OS...and it seems really polished.  But I can't get it to use an external monitor!!

I've installed Ubuntu on an external drive and got it and the cool Compiz stuff to work on my laptop (I have a Dell XPS M1210).  I needed to check the box that said to use the restricted drivers...once I did that everything seemed to go OK -- although it took me a couple hours to figure out I didn't install the advanced effects settings,

At this point, I am just trying to get my laptop to run Ubuntu on the external monitor I have at home.  Under Windows XP, I usually just plug in my monitor and hit Fn-F8.  Tried that and it didn't work....then I found the "Screens and Graphics" settings under System->Administration.  I enter my monitor's info under Screen 2 (Samsung Syncmaster 226bw) and clicked that it should be the default screen...clicked OK.

The system told me to log off, which I did.  When I logged off the screen went blank and I got a funky dialog box saying that the system is running in low resolution mode...I hit the configure button and re-keyed in my monitor info, etc.  When it came up it was in low resolution mode anyway.  Plus my monitor info was gone!!!  Plus my advanced desktop effects were off.  When I turned the effects on it said I needed to enable the nVidia driver...which I swore I had already done to get the cool effects in the first place.

The the system said I needed to reboot, which I did.  When it came back up my other monitor info was gone again.  So I reentered it...and it asked my to log off and the whole process repeated.  I've tried this about 10 times and have to say have already spend more time screwing around with Ubuntu in 2 days that I have with Windows in the past year.  Maybe its me...I want to make it work.

Any help is appreciated....but remember I am a total newbie...

---

### Post by jimjan on 2007-11-05
really hope we get some sound info collected in one spot for this issue; i have dell desktop with crt monitor e773c and can not get it to work;

hope we can get this fixed

how do we get this in front of the devs for info now and then avoid in heron?

a linux user but going to vector live cd for now

---

### Post by HDave on 2007-11-06
Thinking that perhaps it was compiz, I redid my installation of Ubuntu from scratch, enabled the restricted drivers for nvidia, and tried to get the external monitor working.

Bottom line, I enter my monitor (this time a DELL 2407wpf) into the Screen 2 and it just stays dark.  But now my laptop screen shows the bars at the top and bottom of the window, but the background is black.  

Now when I log in and log off my screen resolution is reset to 800x600.

This is really frustrating...it seems as though Ubuntu simply doesn't support driving an external monitor from a laptop...but I can't believe that.

---

### Post by pd71sat on 2007-11-09
> **HDave said:**
> Thinking that perhaps it was compiz, I redid my installation of Ubuntu from scratch, enabled the restricted drivers for nvidia, and tried to get the external monitor working.

Bottom line, I enter my monitor (this time a DELL 2407wpf) into the Screen 2 and it just stays dark.  But now my laptop screen shows the bars at the top and bottom of the window, but the background is black.  

Now when I log in and log off my screen resolution is reset to 800x600.

This is really frustrating...it seems as though Ubuntu simply doesn't support driving an external monitor from a laptop...but I can't believe that.

HDave I have the exact problem that you describe only it is with a AMD64-3500 Desktop system with ATI Radeon X700 Pro Graphics card and an old Viewsonic PF775 CRT monitor. I had everything working fine after I did the installation of the ATI/AMD graphics proprietory driver(8.40), XGL compiz, etc. I installed Gutsy afresh on a second SATA Hard drive in the machine. Windows XP is onthe first HD and I use the bios boot selection to go to whichever OS I want at boot time. I do it this way such that if a family member want to use the machine it will boot to Windows by default. 

My problem started last night when I wanted to lower the screen resolution for readability. It took a default of 1600x1200 for my 17" CRT monitor. The monitor is spec'd for that resolution but I wanted to go to 1152x1024 resolution or something to that effect. I did the "Screens and Graphics" settings under System->Administration as you did and on reboot I am into the same scenario. To get back to my original situation I know I can re-install the ATI driver ( I still have the *.deb package in my home dir) and I expect that that can get me back to the initial config that worked. Maybe I can shortcut and just do the "aticonfig --initial", etc  stuff and continue on from there. 

Ultimately though I just want a comfortable resolution for my eyes and gutsy is not allowing me to do that even though I am starting from a working config. I suspect it has something to do with the screen resolutions that are present in "/etc/X11/xorg.conf". 

Thanks for any pointers to get beyond this low resoltuion graphics loop.

---

### Post by HDave on 2007-11-09
pd71sat -- I have been reading up on our (and other) problems using external monitors with Gutsy.  I hate to say it, but it seems that everybody who has gotten past their issues has had to manually edit their xorg.conf file.

This file is pretty scary looking and full of stuff  I don't understand, so I am trying to learn more before I start hacking away.

Here is a helpful thread I found regarding a problem that seems somewhere between yours and mine..

[http://ubuntuforums.org/showthread.php?t=599443&highlight=external+monitor]("http://ubuntuforums.org/showthread.php?t=599443&highlight=external+monitor")

---

### Post by pd71sat on 2007-11-10
I now have a handle on the issue on the problem that I had. Option System-->Administration-->[COLOR="Red"]Screens and Graphics[/COLOR] breaks the xorg.conf file. This may be specific to the ATI Graphics Cards but I do not know for sure.

In poking around for options I stumbled on Applications-->Accessories-->"ATI Catalyst Control Center". Clicking it tells me that it is not functioning and should be re-installed. In windows I use the Catalyst Control to set up my graphics options and displays and so I thought that this held the key to my problem. So I set about rectifying my situation using [[COLOR="Blue"]this post (entry #201)[/COLOR]]("http://ubuntuforums.org/showthread.php?t=221320&page=21") by Alex Fernandez. I used **method 2** with some modifications that I am detailing in these steps:

1) Previously I had added "**fglrx**" to the restricted drivers list after installing with the October .iso package. Since that time I had done a distribution upgrade to get updated modules. Maybe that  had reset the file. Anyway do as the post says, and I did again.

2)  For the step "bash <the ati.run file name> --buildpkg Ubuntu/feisty" substitute "**gutsy**" for "feisty".

3) At this point before running "sudo dpkg -i *.deb" I did this:

     **sudo apt-get purge xorg-driver-fglrx**

I read in some other post, that does not come to mind, that bad performance could result from having mismatched files. I tested my FPS with "glxgears" before and after the ATI drivers install and it went from 5000 odd to over 10000, so there could be some truth to this! 

4) Continue with the install. By the way I had had a copy of the "**ati-driver-installer-8.40.4-x86.x86_64.run**" file from in August as I was building my daughter's Laptop then. That is the file I used here on my desktop. I see that there are problems with the 8.42 drivers and beyond. 

5) Before step 2) in the post I run the following to preselect the screen resolutions in my "xorg.conf" file:

**sudo dpkg-reconfigure -phigh xserver-xorg**

Luckily I had my Viewsonic PF775 User's Guide handy and I found the section which showed the valid screen resolutions. If you do not have your manual then maybe you can find a softcopy on the manufacturer's website. Good luck! Now continue with step 2) in the post.

5) Now that you are finished and have a working system there some points that you may be aware of;

The "/etc/X11/xorg.conf" file has two monitor sections titled "**Generic Monitor**" and "**aticonfig-Monitor[0]**". These are matched to two Device entries, titled "**ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]**" (PS: Your device name string will be different depending on the ATI card installed) and "**aticonfig-Device[0]**", in the Screen bindings sections, titled "**Default Screen**" and "**aticonfig-Screen[0]**".

I see no reason to have a mismatch and to not use the proprietory driver to power both devices so I changed the first device's Driver to "fglrx" as well. Secondly I noticed that my Screen "**aticonfig-Screen[0]**" had the following line with the screen resolutions I selected before:
Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480" (PS: Yours will depend on the selections you made earlier). Again I see no reason to have a mismatch so I copied this to the "**Default Screen**" section. Hers is what my good "xorg.conf" look like:
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

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
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
	Option	    "XkbVariant" "intl"
	Option	    "XkbOptions" "lv3:ralt_switch"
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
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 80.0
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
	Identifier  "ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Driver      "fglrx"
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
	Device     "ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
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
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Extensions"
Option "Composite" "0"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection

```

I made sure I saved my good working "xorg.conf" file. Now that I got the ATI proprietory driver working again I enabled the "Restricted Driver Manager". I took the preacution to reboot even though I was not asked to. Next I enabled desktop effects and voila I had all those wobbly windows etc.

For the heck of it, confident that I had my "xorg.conf" file saved, I tried to set my screen resolution again; System-->Administration-->[COLOR="Red"]Screen and Graphics[/COLOR]. I noticed that the re-install now showed a default of 1021x768. Acceptable but I wanted to see what happens when I chose 1152x864. 

Once done and reboot I was back into the same low resolution graphics scenario and funny lines on the screen on initialization. I proceeded to full logon at 800x600 graphics mode and checked my "xorg.conf". Here is what I found:
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
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

As you can see the good "xorg.conf" file has been replaced with a bad one and I am into this mesa crap situation again. For me the solution was simple. I simply copied back my saved good "xorg.conf" file and rebooted and all was back to normal. Even the "Restricted Drivers Manager" was found to be enabled again without my having to touch it. Compiz fusion effects were also back. Simple eh!

So my only problem is that I am stuck with the resolution that the install picked. 1024x786 is good for me luckily as that is what I use on Windows. So do not try to use the "[COLOR="Red"]Screens and Graphics[/COLOR]" option to change your screen resolution until we can get a handle on why it breaks the "xorg.conf"! Hope this helps someone else to avoid the mesa crap.

By the way the Applications-->Accessories-->"ATI Catalyst Control Center" still tells me that it is not installed? Wonders that I now ignore.

---

### Post by HDave on 2007-11-14
Thanks for the info.  I suspected that the screens and graphics GUI was hosing the xorg.conf file...nice to see proof.  This seems to me to be a major bug in Ubuntu I hope somebody fixes soon.

I didn't mention it, but my laptop is has an NVIDIA GE Force Go 7400, so my installation procedure will be very different from one for ATI graphics cards.

I found an NVIDIA website that looks like it has all the information one would need to get one of their graphics cards running under Linux.  However, its a LOT of reading and its not specific to Ubuntu.  Check it out:

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8756/README/index.html]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8756/README/index.html")

I also found a link to some documentation regarding the structure of the xorg.conf file.  Apparently Xorg is the group that maintains the X windows system these days after a licensing spat with XFree86 (or something like that).  At any rate, that link is as follows:

[http://ftp.x.org/pub/X11R6.9.0/doc/html/xorg.conf.5.html]("http://ftp.x.org/pub/X11R6.9.0/doc/html/xorg.conf.5.html")

I am in the process of going to school on Xxorg.conf and NVIDIA and hopefully will have some progress to report back sooner or later.

---

### Post by HDave on 2007-11-14
After much reading on the nVidia website, I have found the latest set of docs to do with the most recent driver release which is version 100.14.19 which can be found here:

[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/index.html]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/index.html")

...a much newer link the the one I posted above...  :)

---

### Post by pd71sat on 2007-11-16
HDave, glad to see that you have some info that can help you. Hope you resolve your Nvidia card specific issue soon.

I ran into a minor problem recently after doing an install of IBM's DB2 V9.1 Database Server software. I suddenly found that my display switched back to the highest resolution of the monitor i.e. 1600x1200. My 17" CRT screen was nearly impossible to read at this resolution. About a day ago I got the idea to delete the extra resolutions beyond 1152x864. This morning I booted into recovery mode and did just that. Now that I am up, the system chose the 1024x768 resolution again. 

I guess that I am happy again as a pig in mud. I won't complain that it never took the 1152x864 that was my goal initially. My screen is readable again and I am good to go.

---

### Post by HDave on 2007-12-05
OK -- After a few more weeks of reading and testing I discovered that solving my problem was incredibly easy.  The key to getting this to work is a tool call nvidia-settings.

I figured this out early, but I got very confused because there is a synaptic package called "nvidia-settings, but for some reason it is related to an older driver than nvidia-glx-new.  if you install this package it automatically removes the good driver!!!  Bug -- if you ask me.  So don't install it.

Apparantly the correct version of nvidia-settings is automatically installed as part of the restricted drivers package (nvidia-glx-new).  I had only to run it.  DOH!!!  :(

The next thing that tripped me up is the Screens and Graphics admin tool.  I don't know WHAT is up with that thing, but it is very busted and will destroy your xorg.conf file.   So don't use it -- another bug.  :mad:

The last thing is that the nvidia-settings program is quite temperamental.  Essentially if you want to drive an external monitor from your laptop you need to:

1) plug in the monitor
2) run nvidia-settings
3) (optional) scan for monitors if it doesn't see it
4) enable the external monitor and manually set the refresh rate (60Hz for me)
5) DISABLE THE LAPTOP SCREEN
6) REBOOT

My comments:
a) Why disable the laptop screen, why not enable the Fn-F8 key?  who knows?
b) even though you have disabled the laptop screen when you boot without a monitor plugged in it will still use it!   YAY!!!
c) When you change external monitors it will do the right thing and adjust resolution.  Double YAY!
d) why can't I just restart X...why reboot?  who knows?

Anyway thats it...

---

