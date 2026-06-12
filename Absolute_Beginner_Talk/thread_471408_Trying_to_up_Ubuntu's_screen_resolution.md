---
title: "Trying to up Ubuntu's screen resolution"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by peter_k on 2007-06-12
I'm wondering why Ubuntu (7.04) will only let my resolution go up to 1024x768; I was able to run 1280x1024 in Mandriva, so my resolution should support it, and I believe it worked in the LiveCD environment at 1280x1024 as well, so I'm pretty sure my card should be supported.

I did a search here, and tried the sudo xconfig trick that's been mentioned.  However, once I got to the point where I chose "VESA" (the default), and then typed in the name of my card (I've tried both Generic and the intel card I have (Intel 82845G/GL/GE/PE/GV Graphics Ctrl)), it shows a screen that looks like this:

Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.  


At that point, I can't hit OK, can't proceed. 

Any ideas?

Peter Knox

---

### Post by overdrank on 2007-06-12
> **peter_k said:**
> I'm wondering why Ubuntu (7.04) will only let my resolution go up to 1024x768; I was a ble to run 1280x1024 in Mandriva, so my resolution should support it, and I believe it worked in the LiveCD environment at 1280x1024 as well, so I'm pretty sure my card should be supported.  In addition, it seems the apps are even bigger (i.e. fonts, window border sizes) than a normal 1024x768 setup.

I did a search here, and tried the sudo xconfig trick that's been mentioned.  However, once I got to the point where I chose "VESA" (the default), and then typed in the name of my card (I've tried both Generic and the intel card I have (Intel 82845G/GL/GE/PE/GV Graphics Ctrl)), it shows a screen that looks like this:

Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.  


At that point, I can't hit OK, can't proceed. 

Any ideas?

Peter Knox

Hi if you choose vesa then dont enter your card name just stick with the default answers until you get to the screen resolutions then add the ones you want. Be sure to restart X after configuring.  After that you can run this command in the terminal *sudo apt-get install xserver-xorg-video-intel* and that should install the proper drivers for the graphics.:popcorn:

---

### Post by Inxsible on 2007-06-12
You can add the resolution that you know your monitor supports in the xorg.conf file in the screens section

post the output of the following command
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by peter_k on 2007-06-12
> **Inxsible said:**
> You can add the resolution that you know your monitor supports in the xorg.conf file in the screens section

post the output of the following command
```
gksudo gedit /etc/X11/xorg.conf
```

Here goes:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Is it just a matter of adding "1280x1024" above in all places in front of "1024x768"?  After this modification, and a save in gedit, that should be it, right (except maybe for a reboot)?

Btw, even though gedit does open xorg.conf, this is what is shown on my terminal screen:

peter@knoxcentral-desktop:~$ gksudo gedit /etc/X11/xorg.conf
(gedit:8700): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-0/socket
This socket already exists indicating esd is already running.
Exiting...

peter@knoxcentral-desktop:~$

Peter Knox

---

### Post by overdrank on 2007-06-12
Hi and yes add the resolution that you want and save and restart X. 
and this is what I get when using the gksudo command 

mineedgy@mineedgy-desktop:~$ gksudo gedit /etc/X11/xorg.conf
(gedit:5812): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

So I believe you are in good shape. Good luck! :D

---

### Post by peter_k on 2007-06-12
> **overdrank said:**
> Hi and yes add the resolution that you want and save and restart X. 


How do I restart X?  Would a reboot do that?

And what would happen if it doesn't work?  Would I get a command prompt or go back to 1024x768?

---

### Post by l951b951 on 2007-06-12
A reboot would work but ctrl+alt+backspace would be easier and wouldn't take as long.

---

### Post by peter_k on 2007-06-12
OK.  I've got the 1280x1024, but it looks like everything is shifted to the right a tiny bit (enough to cut off the "X" in the top right hand corner of firefox, for example, or the trash icon on the bottom desktop bar), and there's a relatively large black line (unusable desktop) on the left (I think more than the shift), and quite a bit of flickering.  When I try to do a screen resolution, it tells me the refresh rate is 43Hz, which sounds incorrect.

I tried to take a screenshot, but in the screenshot you can't see the black bar; it does show the cutting off of the right side though.

---

### Post by zodmaner on 2007-06-12
Try and check your monitor horizontal & vertical sync rate in xorg.conf file. Some times a wrong sync rate can causes this problem.

I have a similar problem, being stuck with 1024x768 resolution and no matter what I do with the driver seems to fixes the problem, until I changes horizontal & vertical sync rate in xorg.conf file to that of my monitor. 

After a reboot it works like charm and I was able to add 1280x1024 to xorg.conf file and use it. No problem with so ever.

[here]("https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29") is the guide that might help you. For info. on how to change the sync rate, look under 'Undetected Monitor Specs'.

Hope this will help. :)

---

### Post by timcredible on 2007-06-12
as for the 'everything is to the right', are you using a digital (dvi) connection?  if not, do that if your video card and monitor support it.  if you're already using a digital connection, refresh rates may be the solution.  if you have an analog monitor (crt), try just moving the screen over on the monitor buttons.  although 43hz sounds too low for any monitor and card, i would try forcing it to 60hz at a minimum.

---

### Post by peter_k on 2007-06-12
Success (but of course with modifications :D )

I did a search for my monitor "eview17f3" on google as stated in the wonderful resources given to me by somebody (I just can't find you in the thread below, but thanks).  It suggested adding a new section to "Monitors" in xconfig, and modifying the Horiz and Vert sync and refresh rates.  It also said to make sure you don't modify the "Generic Monitor" portion, and add your own.  As for that last point, in a word, no (at least for my case).  I modified it as suggested, saved xconfig, and did a ctrl-alt-backspace.  The Xserver did not load, as it was fragged, evidently adding the new section to Monitors made X a very unhappy camper.

Considering I didn't really have a whole lot of time invested, I figured I'd just do a reinstall.  I put in my trusty LiveCD, and then my brain function subroutine must have resumed.  "Why not just modify it on the LiveCD?"  Ithought.  "Sure, it would work as a proof of concept, and in a worse case scenario, I'll just reboot"  I replied (I don't often talk to myself like this, but hey, the subroutine was running. :p

I modified everything in xconfig on the LiveCD, and this time, instead of adding a new section, just modified the "Default Monitor" section - voila -- perfect 1280x1024!  I then did an install, telling myself that I would immediately modify xconfig upon completion of the install.   Now, here's the good part -  <B>I didn't have to.</B>  Evidently the state your system is in during the LiveCD install (I was running it now at 1280x1024) helps determine the state your system will be in after the install.  Brilliant!

Here's the lesson for us newbies -- Keep your LiveCD in a safe place, and make friends with it.  If you want to make a modification that you think might damage your setup, do it on the LiveCD first.  Then, if it doesn't work, you can just reboot and pretend it didn't happen.  Not often do you get a "do over" in life, but here's one case in which you do.

Lesson #2 - don't be afraid of the terminal.  In this thread, I was given a few commands that I was able to cut and paste directly into a terminal session, and just press enter to execute.  If everything was graphical, I would have needed a bunch of screens and a lot more thorough description.

Thanks again everybody!

Peter Knox

---

