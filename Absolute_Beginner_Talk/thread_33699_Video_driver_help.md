---
title: "Video driver help"
date: 2005-05-11
forum: Absolute Beginner Talk
---

### Post by Jace on 2005-05-11
I have a Nvidia Gforce2 mx/400
Screen res is 640x 400
Meaning the driver needs to be loaded. Any help
Keep in mind this is the newbie section and I am a newbie...


Thanks, looks like I am one step closer to never having to buy another MCSE book

---

### Post by crane on 2005-05-11
[QUOTE=Jace]I have a Nvidia Gforce2 mx/400
Screen res is 640x 400
Meaning the driver needs to be loaded. Any help
Keep in mind this is the newbie section and I am a newbie...


Thanks, looks like I am one step closer to never having to buy another MCSE book[/QUOTE]

Try using apt to install nvidia drivers then hit ctrl>alt>backspace to restart X

[Nvidia Install - Ubuntu Guide](http://ubuntuguide.org/#installnvidiadriver) 

What part of the deep south are you from?

---

### Post by Jace on 2005-05-11
Gulf Shores area. Thanks I am a real newbie to this. Can you explain a little more indepth?  Meaning how to use the terminal to install a driver. Let me read into the link you posted. It will probaly have my anser there. Again thanks

---

### Post by Jace on 2005-05-11
ok heres what I did....went to the nvidia driver install link. Followed it . copied and pasted each line into the terminal. Looked like it worked. Went to applications and there is Nvidia setup. Pushed ctrl + alt+ backspace and a screen come up that I could not get out of. Newbie I tell ya. So just like Microsoft cure all, I rebooted. Oh yea I also pasted the text file and hit save into the window that came up. Did I not save it into the right directory??? Thanks

---

### Post by Jace on 2005-05-11
Alright wife is screaming " feed me".. So I must go. I am still @ a very low screen res. Any help would be great.After I shove a cheese burger down her throat I will be right back, why cant they just understand....

---

### Post by i-tech on 2005-05-11
hi ;
try this open synaptic and "search" for nvidia-glx mark and install it. this wil help you i guess. if not we'll think of something else ;-)
enjoy!

---

### Post by Jace on 2005-05-11
Alright I have 1 min. to get this right. I did this and it asked for my ubuntu cd. it looked like it installed it. Still when I go into screen res. it want let me change it. When I go into app> nvidia setting there is nothing there to set screen res.....THANKS

---

### Post by Jace on 2005-05-11
root@LINUX:/home/jason # sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@LINUX:/home/jason # sudo apt-get install nvidia-settings
Reading package lists... Done
Building dependency tree... Done
nvidia-settings is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@LINUX:/home/jason # sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backuproot@LINUX:/home/jason # sudo nvidia-glx-config enable

A backup of xorg.conf has been stored as:
/var/backups/xorg.conf.2005-05-11-20:16:57.
If the new configuration will not work you will be able to
revert the changes simply using this command:
cp /var/backups/xorg/xorg.conf.2005-05-11-20:16:57 /etc/X11/xorg.conf


Warning: your X configuration has been succesfully changed.
In order to take full advantage of the changes, X needs to
be restarted.

root@LINUX:/home/jason # sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

(gedit:9019): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

break

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;


Saved this to   /usr/share/applications

---

### Post by Jace on 2005-05-11
Hey I rebooted the system and now when I go under applications>system tools> nvidia settings is there. Here the kicker...under system> prefs> screen res. It will not let me change the res. Still stuck @ 640x480.....Thanks for the support.

---

### Post by TravisNewman on 2005-05-11
You may have to edit the xorg.conf manually to add in the screen res lines.

My screen section looks like this:
```

Section "Screen"
		Identifier	  "Default Screen"
	    Device		  "NVIDIA Corporation NV17 [GeForce4 MX 460]"
		Monitor		 "Generic Monitor"
		DefaultDepth	24
		SubSection "Display"
			    Depth		   1
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   4
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   8
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   15
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   16
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
		SubSection "Display"
			    Depth		   24
			    Modes		   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		EndSubSection
EndSection

```

---

### Post by csmedsrc on 2005-05-12
I had a similar problem (also a newb).  I got the nvidia driver installed (I have a 6600GT) but my screen resolution is still very low.  I'm going to edit the xorg.conf file but I have another question first.  How can I adjust the refresh rate (its stuck at 60hz in system preferences)?  Also does the default depth line refer to color depth and if so why does it default to 24 instead of 32?  Can you even go up to 32?

---

### Post by csmedsrc on 2005-05-12
OK, I edited the xorg.conf file but I still can't change the resolution under system preferences.  The contents of my edited file are posted below. Could someone please tell me what I am doing wrong.  The only resolutions available under system preferences are "1024x768" "800x600" "640x480" (and yes I did reboot already).  Also please tell me how to change the refresh rate as it is stuck at 60hz right now.  I saw the line for horizontal and vertical refresh but don't know if that's what I need to edit or what refreshrate those settings correspond to.

Thanks



Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
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
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=csmedsrc] How can I adjust the refresh rate (its stuck at 60hz in system preferences)?  [/QUOTE]

By editing the xorg file.

[QUOTE=csmedsrc]Also does the default depth line refer to color depth and if so why does it default to 24 instead of 32?  Can you even go up to 32?[/QUOTE]

32 is a virtual desktop depth. 24 is the same to your human eye. Linux doesn't pretend to be better than the hardware is.

The part that is messing you up is the generic monitor part. You need to delete the 

HorizSync 28-49
VertRefresh 43-72

lines then restart X  (hit alt, ctrl, and backspace at the same time)

---

### Post by csmedsrc on 2005-05-12
Ok. I deleted the lines you mentioned but I still have problems.  First, I am still unable to change the screen resolution and now I am stuck with 640x480 which is even worse than it was before.  Second, the refresh rate is still stuck at 60hz.  How do I fix these problems?

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
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
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by poofyhairguy on 2005-05-12
Oooops sorry mate. Bare with me, and I'll do my best. Try adding these lines in the place where you deleted those lines from:

HorizSync 31.5 - 48.5
VertRefresh 59.0 - 85.0

---

### Post by csmedsrc on 2005-05-12
Well adding those lines got me back to where I was originally.  I can again change the resolution but it only goes up to 1024x768 and the refresh rate is stuck at 60hz.  I added in the new resolutions but for some reason can't switch to them.  Ideally I want my machien at 1280x1024 @ 85hz.  By the way can anyone tell me why my numberpad on my keyboard doesn't work.  Numlock is on but its not working.

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=csmedsrc]Well adding those lines got me back to where I was originally.  I can again change the resolution but it only goes up to 1024x768 and the refresh rate is stuck at 60hz.  I added in the new resolutions but for some reason can't switch to them.  Ideally I want my machien at 1280x1024 @ 85hz.  By the way can anyone tell me why my numberpad on my keyboard doesn't work.  Numlock is on but its not working.[/QUOTE]


Try deleting the 1600x1200 line (making 1280x1024 the first one) and try restarting x...

---

### Post by csmedsrc on 2005-05-12
Tried it, but it didn't do anything.

---

### Post by poofyhairguy on 2005-05-12
I need to know something. Can you replace the word nvidia on teh drivers line with "nv" please? then restart x and tell me what happens.

---

### Post by csmedsrc on 2005-05-12
The only thing that happens is that my screen moved over about a 1/4 of an inch and I had to readjust my monitor.  I still can't change the resolution or refresh rate.  Oh one more thing.  I'm not quite sure when in this process it started by after awhile I couldn't restart x anymore.  The screen would go black and I was asked for my user name and password and then it would tell me I had new mail but the screen was still black and I wasn't logged into gnome.  Because of this I now just restart the machine.

---

### Post by poofyhairguy on 2005-05-12
Darn. It works great on mine. the only other difference I see is in the device section. here is mine:

> Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option		"NoLogo"
	Option 		"RenderAccel" 		"true"
	Option 		"AllowGLXWithComposite" "true" 
EndSection 

You are missing two lines I have.

---

### Post by Arjen on 2005-05-12
I don't think the RenderAccel and AllowGLXComposite will help in this case. They are only meant to make use of certain aspects of your videocard. And last time I checked, nVidia still claimed RenderAccel might cause problems. Not that I've ever encountered any of them though.

While I can't come up with a solution for the resolution, the refresh rate I probably do know how to fix. But you'll have to look in the manual of your monitor for it.
If you look at the technical specifications you should see the vertical and horizontal refresh rates your monitor can handle. If you use these values in the HorizSynce and VertRefresh mentioned by poofyhairguy it should allow you to use all of refresh rates your monitor can handle.

Now that I think about it, this might also help with the resolution, but don't quote me on that.

---

### Post by Jace on 2005-05-12
Exact same issue I am having, did you check your new mail????????

---

### Post by Jace on 2005-05-12
Would I be running into these issues with KUbuntu?   [Newbie question]

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=Jace]Would I be running into these issues with KUbuntu?   [Newbie question][/QUOTE]


Kubuntu uses the same Xserver Ubuntu does, so yes. You have another option (its what I did to fix my girlfriends laptop with the same problem). Get a SUSE, or mandrake), or Knoppix (thats the one I used) LIve CD and run it. If the resolution is what you want, open the xorg.conf file (its called Xfree86.conf in knoppix) and copy it into a new file that you save onto a disk. Then boot back into about and copy the contents of that file into Ubuntu's xorg.conf file (after backing it up of course). The restart x (alt, crtl, backspace) and everything should work. Knoppix (and other live cds) have better video detection than Ubuntu.

---

### Post by Jace on 2005-05-13
This is my file. See anything?

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Visual Sensa"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Visual Sensa"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=Jace]
Section "Monitor"
	Identifier	"Visual Sensa"
	Option		"DPMS"
EndSection
[/QUOTE]

The problem is here. Try to make it look like this:


[QUOTE=Jace]
Section "Monitor"
	Identifier	"Visual Sensa"
        HorizSync 31.5 - 48.5
        VertRefresh 59.0 - 75.0
	Option		"DPMS"
EndSection
[/QUOTE]

---

### Post by Jace on 2005-05-14
Works great. It took me a second to remember the steps, you guys did great making the steps "click" for me. Time to move on to the next step. Again Thanks....

---

### Post by poofyhairguy on 2005-05-14
[QUOTE=Jace]Works great. It took me a second to remember the steps, you guys did great making the steps "click" for me. Time to move on to the next step. Again Thanks....[/QUOTE]


Good deal. Thanks for your patience.

---

