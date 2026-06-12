---
title: "Trying to run before I can walk"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by mgbridges on 2007-11-19
Hi folks,

I've just installed Ubuntu 7.10 Gutsy Gibbon on my home desktop PC. In the past I've tinkered a bit with other forms of Linux but never really got stuck into it. This time I was forced into it - I had to replace my motherboard and I had an OEM license for Windows XP so I couldn't move the OS across. Rather than pay for a new license I decided to go with Ubuntu as it had been recommended to me.

The installation went smooth as you like. I was very impressed with how easy it went. Within half an hour or so I had the PC up and running and connected to my wireless network. I think I then got a bit carried away and things are looking a bit messy.

I'll just quickly outline my system:
Asus M2A-VM HDMI motherboard (with ATI X1250 graphics onboard)
AMD Athlon X2 4800 dual-core CPU
2Gb memory
Terratec DMX 6fire 24/96 soundcard

I think part of my problem is that there is so much good documentation out there. This has given me (misplaced?) confidence to try and do stuff that perhaps I should have waited for! Here are some of my difficulties:

- tried to install ATI driver for onboard video card. I've followed various online documents, downloaded packages etc. My display works OK but there's something not right. For example, Google Earth won't even launch and is complaining about missing OpenGL libraries.

- tried to install Azureus bittorrent client. As part of this, tried to install new version of Java and SWT. Azureus still won't launch.

- bought Open Sound System application as it supposedly provides drivers for my soundcard. I get sound OK (although I haven't tried all the features of the soundcard) but there's an icon in the status bar complaining about something to do with sound.

I'm thinking I should just stick to doing things via the GUI, as the command line is allowing me to mess things up big style!

Does anyone have any suggestions on how to deal with the problems above. Or at the very least, how to revert my system to a simple working state!

Many thanks,

Martin

---

### Post by Phesto on 2007-11-19
> **mgbridges said:**
> 

- tried to install ATI driver for onboard video card. I've followed various online documents, downloaded packages etc. My display works OK but there's something not right. For example, Google Earth won't even launch and is complaining about missing OpenGL libraries.

- tried to install Azureus bittorrent client. As part of this, tried to install new version of Java and SWT. Azureus still won't launch.

- bought Open Sound System application as it supposedly provides drivers for my soundcard. I get sound OK (although I haven't tried all the features of the soundcard) but there's an icon in the status bar complaining about something to do with sound.



For the ATI problem, i think it would help if you posted your xorg.conf file so we could see what is actually going on there. The file can be found at /etc/X11/xorg.conf you can just open it up in any txt editor copy the contents and paste in a post

The Azureus problem, if it is that it begins to start and then crashes with a core dump could be this issue that i experienced and you can find the solution here 

[http://ubuntuforums.org/showthread.php?t=580028&highlight=azureus](http://ubuntuforums.org/showthread.php?t=580028&highlight=azureus)

The last issue with the sound, you need to post the actual error because without that i don't know where to begin making suggestions.

Hope this helps.

---

### Post by mgbridges on 2007-11-19
> **Phesto said:**
> 
The Azureus problem, if it is that it begins to start and then crashes with a core dump could be this issue that i experienced and you can find the solution here 

The error I'm getting when I try to start Azureus is:
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-gtk-3346 or swt-gtk in swt.library.path, java.library.path or the jar file

I realised after I'd posted that I was a bit vague on the other issues. I will add some more detail when I get home tonight and can dig the necessary files out.

Thanks for your help so far.

Martin

---

### Post by jaybombalous on 2007-11-19
there are better torrent clients out there for linux then azureus. I would first try one like Ktorrent or deluge. Work a lot better under linux.

---

### Post by mgbridges on 2007-11-19
> **jaybombalous said:**
> there are better torrent clients out there for linux then azureus. I would first try one like Ktorrent or deluge. Work a lot better under linux.

That's a reasonable thought. I quite liked Azureus on Windows, hence my attempt to use it on Linux. I guess I could try something else!

Martin

---

### Post by mgbridges on 2007-11-20
> **Phesto said:**
> For the ATI problem, i think it would help if you posted your xorg.conf file so we could see what is actually going on there. The file can be found at /etc/X11/xorg.conf you can just open it up in any txt editor copy the contents and paste in a post.

Here it is:

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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"Generic Video Card"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:5:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"PLE481S"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"PLE481S"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x960@85"	"1024x768@43"	"1280x1024@85"	"1024x768@60"	"1280x1024@60"	"1024x768@70"	"1280x960@75"	"1024x768@75"	"1400x1050@60"	"1024x768@85"	"1400x1050@75"	"832x624@75"	"1600x1200@65"	"800x600@60"	"1600x1200@60"	"800x600@85"	"1600x1200@75"	"800x600@75"	"1600x1200@70"	"800x600@72"	"1792x1344@60"	"800x600@56"	"1856x1392@60"	"640x480@85"	"1920x1440@60"	"640x480@75"	"2048x1536@60"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"dri"
	Load		"v4l"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
	Option		"Composite"	"0"
EndSection
Section "ServerFlags"
EndSection

---

### Post by mgbridges on 2007-11-20
> **Phesto said:**
> The last issue with the sound, you need to post the actual error because without that i don't know where to begin making suggestions..

The error message I get is:

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.


Thanks for all your help so far.

Marftin

---

### Post by zvacet on 2007-11-20
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by mgbridges on 2007-11-20
> **zvacet said:**
> [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Sorry if I'm being clueless, but I have no idea how this is relevant to the issue I'm having. Can you please explain a bit rather than just posting a URL?

Thanks,

Martin

---

### Post by Mazza558 on 2007-11-20
> **mgbridges said:**
> Sorry if I'm being clueless, but I have no idea how this is relevant to the issue I'm having. Can you please explain a bit rather than just posting a URL?

Thanks,

Martin

That link would install the restricted codecs (e.g video/sound codecs) that could be the problem.

---

### Post by mgbridges on 2007-11-20
> **Mazza558 said:**
> That link would install the restricted codecs (e.g video/sound codecs) that could be the problem.

I did that before I did anything else. The problem seems to be related to the installation of the ATI driver, which I'm not sure completed successfully.

Any other ideas based on the .conf file I was requested to post?

Martin

---

### Post by KhaaL on 2007-11-20
Heya man! 

I recognise the ATI openGL problem - I think I had the same problem in my laptop. Could you type the exact error you get?

Hang in there, you'll be leaping before you realize that you're running! ;-)

---

### Post by markharding557 on 2007-11-20
> **mgbridges said:**
> The error I'm getting when I try to start Azureus is:
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-gtk-3346 or swt-gtk in swt.library.path, java.library.path or the jar file

I realised after I'd posted that I was a bit vague on the other issues. I will add some more detail when I get home tonight and can dig the necessary files out.

Thanks for your help so far.

Martin

have you got java installed it is not installed by default in ubuntu

---

### Post by mgbridges on 2007-11-20
> **markharding557 said:**
> have you got java installed it is not installed by default in ubuntu

Yes, I specifically downloaded the 645-bit version from the Sun website. I think it inbstalled OK - is there any way to check?

Martin

---

### Post by KhaaL on 2007-11-20
Type:
java -version

In a console and see what it returns.

---

### Post by master_kernel on 2007-11-20
Hi,

I have almost the same exact system as you:

ASUS M2A-VM motherboard
AMD Athlon 64 4800+ Brisbane
Integrated High Definition Sound

For your Google Earth and Azurus problems, I'm pretty sure both are dependent on Java. Since Java does not like 64-bit systems, I have not been able to successfully get these programs to work. There is a member on this forum--Kilz--who is great with 64-bit stuff.

---

### Post by mgbridges on 2007-11-21
> **KhaaL said:**
> Type:
java -version

In a console and see what it returns.

The response is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

Is this the right version? I'm running 64-bit version of 7.10 on an AMD64 x2 system.

Martin

---

### Post by mgbridges on 2007-11-21
> **KhaaL said:**
> Heya man! 

I recognise the ATI openGL problem - I think I had the same problem in my laptop. Could you type the exact error you get?

Hang in there, you'll be leaping before you realize that you're running! ;-)

Thanks for persevering with me! The error I get when I try to start Google Earth from the command line is:

./googleearth-bin: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


Martin

---

### Post by KhaaL on 2007-11-21
To redeem the libGL library problem, try:

ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

And see what happens...

Oh, and in order to spare yourself as much headache as possible, run the 32 bit ubuntu or look for answers in the 64bit forum [here]("http://ubuntuforums.org/forumdisplay.php?f=134")

---

### Post by mgbridges on 2007-11-21
> **KhaaL said:**
> To redeem the libGL library problem, try:

ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

And see what happens...

Oh, and in order to spare yourself as much headache as possible, run the 32 bit ubuntu or look for answers in the 64bit forum [here]("http://ubuntuforums.org/forumdisplay.php?f=134")

Thanks - I'll try that this evening when I get home.

I actually installed the 64-bit version because I naively thought that it would run better on my Athlon64 system. It certainly seems that the 64-bit version makes things trickier (due to being newer and with less in terms of drivers and programs etc.).

I daren't try and go back to 32-bit though!

Martin

---

### Post by mgbridges on 2007-11-22
> **KhaaL said:**
> To redeem the libGL library problem, try:

ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

And see what happens...


Tried it. No joy, same error message as before.

Martin

---

### Post by Joeb454 on 2007-11-22
Like other people have said, the 32 bit systems generally have more support in terms of hardware and software. The only reason 64 bi system don't is that not many people have started using them properly yet, that and developers can be lazy and don't want to move their code over to 64 bit instructions :p

---

