---
title: "[SOLVED] Monitor out of range"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Miau00 on 2008-02-24
Hello,

Somehow I have successfully managed to install Kubuntu. I'm posting from it right now :D

I have a small problem, however, which did not present itself in the live CD. Whenever I start Kubuntu, my monitor goes black and displays the below message:

46 . 4 khz / 87 hz
OUT OF RANGE

This only lasts a few seconds. Soon the log-in screen comes on, and I have no further problems. When I reboot the same thing happens. I tried the solution offered [here]("http://www.hotubuntunews.com/blog_03.shtml"):
> sudo dpkg-reconfigure xserver-xorg

...
 
After configuring your hardware, you will be asked to configure your monitor ... there will be a screen that will tell you the merits of each of the three config options -- Simple, Medium, and Advanced -- you want to select 'Advanced' 
 
For your Horizontal refresh rate, set as '60-70' (without the quotes) 
 
Set your Vertical refresh rate as '70-160' (without the quotes) 

... which made it all worse. My view area was cut off and my screen flickered horribly. Finally I managed to dig out the monitor user guide and found out that the default options were already the ideal for my model (30-80 vertical, 56-75 horizontal). I've reset everything and my screen works all right, except for that error message everytime Kubuntu starts up.

Does anyone know what the problem could be and how to fix it?

I'm sorry if I didn't provide enough details. I'm a n00b when it comes to this :(

Thank you.

**Edit**: Solution here:
[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

---

### Post by oedha on 2008-02-24
what about sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Miau00 on 2008-02-24
Thank you for the quick reply. After doing that I get this:
> xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in etc/X11/xorg.conf.<xxxx>
I can perceive no change: the "Out of range" message still comes up.

---

### Post by Mustard on 2008-02-24
When diagnosing a problem like this the first step is usually to show someone your xorg.conf file.  Open a terminal and use the command below.

```
kate /etc/X11/xorg.conf
#this will display the xorg.conf file in your kate application
```

Copy and paste the contents of your xorg.conf file into this thread using the special forum codes to enclose your pasted text.

Example.


[noparse]```
..your text pasted in here..
```[/noparse]

Using the [noparse]```
..
```[/noparse] forum codes for these types of config files is important so that are displayed 'as is' without the forum altering them in any way.

---

### Post by Miau00 on 2008-02-24
```
Section "Files"
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
	Identifier	"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"L1722P"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS480 [Radeon Xpress 200G Series]"
	Monitor		"L1722P"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Thank you for your time.

---

### Post by Mustard on 2008-02-24
Ok.. a couple of questions...

1. Do you have the manual for your monitor and does it show the frequency ranges for vertical refresh and horizontal synch?  
1b. If so what does the manual say they are?

2. If you don't have a manual, can you use google to search for your make and model of monitor and find the vertical refresh and horizontal synch settings?

I'm just not sure where you got the settings you mentioned in the above post, if they are the manufacturers recommended settings then we can use them I suppose.

I can link you to a good guide for fixing these types of settings and making them more specific to your monitor.  I'm making an educated guess that this might help fix the problem.

This is the link to the 'How to' I'm looking at...

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

There are section in there on manually inputing your Horiz/Vert settings, as well as creating specific modelines for your resolutions.  I would read over it first and come back with any questions you might have about things that need clarifying.  I'll try to help with clarification, but my knowledge is pretty limited myself. :)

**Its important to backup your original xorg.conf before you start fiddling with it.  It makes recovering from an error a lot easier. Read how to make a backup of your xorg.conf in that 'HOW TO' guide**

---

### Post by Miau00 on 2008-02-24
> 1. Do you have the manual for your monitor and does it show the frequency ranges for vertical refresh and horizontal synch? 
  1b. If so what does the manual say they are?Here is the relevant info I found under a section titled "Specifications":
  
  **Sync Input**
  Horizontal Freq. 30-83Hz (Automatic)
  Vertical Freq. 56-75Hz (Automatic)
  
  **Resolution**
  Max
  DVI Digital: VESA 1280x1024@60Hz
  D-sub Analog: VESA 1280x1024@75Hz
  Recommended VESA 1280x1024@60Hz
 
 > sudo dpkg-reconfigure xserver-xorg
 
 ...
 
 After configuring your hardware, you will be asked to configure your monitor ... there will be a screen that will tell you the merits of each of the three config options -- Simple, Medium, and Advanced -- you want to select 'Advanced'Using "Advanced" I entered the frequency ranges. Well, I didn't have to. The default ranges already matched the specifications in my monitor's manual. I looked in xorg.conf again and these numbers are present. The monitor still displays an out of range message. Then I tried "Medium" and chose the manual's recommended setting of "1280x1024@60Hz." No difference. I even tried extending the frequencies (both v. and h. since I didn't know which one was reported) to 87&#8212;the number reported in the error message: 46.3 (or 46.4) khz / 87 hz. No difference.

Ah, this is a bit too much to deal with at 1:30 a.m. ;) I'll retire for now.

I greatly appreciate your help. Thank you.

---

### Post by Mustard on 2008-02-24
> Ah, this is a bit too much to deal with at 1:30 a.m.  I'll retire for now.

I know that feeling. :)

Looking at your xorg.conf file above I dont see the the Vert/Horiz settings in there..

Your current xorg.conf has this...

```
Section "Monitor"
	Identifier	"L1722P"
	Option		"DPMS"
EndSection

```

What I think you might need to add is these lines...

```

Section "Monitor"
	Identifier	"L1722P"
	Option		"DPMS"
        HorizSync     30-83
        VertRefresh    56-75
EndSection

```

This may well stop the monitor from switching from an unusable to setting to a useable one, by starting it in the useable setting first time.  If that makes sense. :)

I'm not sure what the ' Option "DPMS" ' means, but I assume its necessary.  I may be wrong.

If you wanted to edit your xorg.conf rather than just viewing it, you would need to open it with the addition of a sudo command

Make a backup first

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup0001
#what you call the backup is not really that important, 
#just as long as you know which backup you last saved so perhaps substitue the date for '0001' instead
#maybe call it xorg.conf_backup240208

```

To edit..

```
sudo kate /etc/X11/xorg.conf
#this should open xorg.conf as a 'superuser' allowing you to edit and save the new configuration

```

Add the new lines making sure that you pay attention to correct syntax like capital letters, quotation marks etc..save the file and restart the xserver using ctrl+alt+backspace.

---

### Post by angrboda on 2008-02-24
Hi,

most modern monitors can communicate their specs to the system (EDID). If not explicitly switched off your xserver will use this option, thereby overriding the freqency settings you put in your xorg.conf.
In some cases the info the device sends is wrong (though in most cases they would be too conservative rather than too risky... but, well...)
If that is the problem try to add the the following to "monitor" section of your xorg.conf:
```

Option          "UseEDIDFreqs"  "false"
```.

That way your freq settings will be used. Be sure you have the correct settings. Using a frequency range that exceeds your monitors specs can damage it!

Hope that helps.

EDIT: @ Mustard: DPMS is the poweersaving option. It should stay.

---

### Post by angrboda on 2008-02-24
And yes: if the xorg.conf you posted above is what you are using you'll have to insert the HorizSync and VertRefresh lines as Mustard said...

---

### Post by Miau00 on 2008-02-24
Hello,

[QUOTE=Mustard]What I think you might need to add is these lines...[/QUOTE][QUOTE=angrboda]If that is the problem try to add the the following to "monitor" section of your xorg.conf[/QUOTE]The relevant section of xorg.conf now looks like this:

```
Section "Monitor"
	Identifier	"L1722P"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
	Option          "UseEDIDFreqs"  "false"
EndSection
```Did ctrl+alt+backspace, rebooted. Unfortunately, I still have the same problem.

I'm not sure if it's related, but I have another monitor problem. The screen is far too bright and washed out. On this forum the stars next to user names that mark a person as online, for example, appear almost white. The text on [this site](http://www.opendesigns.org/) is almost invisible. I don't have this problem on Windows (I'm dual-booting). Adjusting my monitor settings doesn't solve it. I tried adjusting the gamma under System Settings>Monitor & Display>Color & Gamma. No luck. **EDIT**: Fixed by installing the ATI accelerated graphics driver.

I'm guessing Kubuntu and my monitor just don't get along :(

---

### Post by erginemr on 2008-02-24
Hi,

This problem has nothing to do with the xorg.conf file; it is what is known as a usplash problem. Please refer to this howto for a solution:

[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

---

### Post by Miau00 on 2008-02-24
> **erginemr said:**
> Hi,

This problem has nothing to do with the xorg.conf file; it is what is known as a usplash problem. Please refer to this howto for a solution:

[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)Solved :D

Thanks everyone for your help!

---

### Post by erginemr on 2008-02-25
> **Miau00 said:**
> Solved :D

Thanks everyone for your help!

You are welcome. Take care and have fun with Ubuntu. ):P

P.S. To mark your thread as solved, you can use the "Thread Tools" menu at the top of this page.

---

### Post by HoLLyw00dGT on 2008-03-02
Would any of this have anything to do with my monitor issue? I have a 32" LCD, it says no signal in ubuntu. (It worked before when i installed it like 4 days ago, but had 2 uninstall due to dual boot issues) Anyway, it shows up on my 15"crt.
 Related?
-Justin

---

### Post by erginemr on 2008-03-02
> **HoLLyw00dGT said:**
> Would any of this have anything to do with my monitor issue? I have a 32" LCD, it says no signal in ubuntu. (It worked before when i installed it like 4 days ago, but had 2 uninstall due to dual boot issues) Anyway, it shows up on my 15"crt.
 Related?
-Justin

You need to give us more details:

1- Which part doesn't work? When does it say no signal, during boot? Does the screen come back at the login screen, or does the "no signal" issue persist forever and you are unable to see the desktop?

2- "but had 2 uninstall due to dual boot issues" Please explain this further.

3- What is the natural resolution of your 32" LCD? Wow, this is a TV monitor I guess?

---

### Post by HoLLyw00dGT on 2008-03-02
Well it doesn't say no signal after i change the resolution and stuff on my crt and switch to my 32". Oh and yea it's my HDTV i just use it as my monitor as well. So yes I HAVE signal now BUT some other problems persist. It's natural resolution is 1366 x 768. I think on windows i use it as 1360 x 768 and nothing gets cut off. Right now it is on LCD panel 1024x768 at 55Hz. What do i need to do to make my left side of my screen not cut off. For example, the button in the bottom left that hides all of the windows...i can only see about half of it.

---

### Post by erginemr on 2008-03-02
OK. Can you please run this command from the terminal:
```
gedit /etc/X11/xorg.conf
```
copy what is inside this file and paste it here?

Please also paste the output of this command here, too:
```
lspci | grep -i vga
```

Also tell me when exactly it says "no signal", during boot when you don't use the CRT screen? Are you able to see the Ubuntu splash screen with the orange progress bar on your HDTV screen (but without using the CRT screen to set things right)?

---

### Post by HoLLyw00dGT on 2008-03-02
> **erginemr said:**
> OK. Can you please run this command from the terminal:
```
gedit /etc/X11/xorg.conf
```
copy what is inside this file and paste it here?

Please also paste the output of this command here, too:
```
lspci | grep -i vga
```

Also tell me when exactly it says "no signal", during boot when you don't use the CRT screen? Are you able to see the Ubuntu splash screen with the orange progress bar on your HDTV screen (but without using the CRT screen to set things right)?

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

Section "Files"
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
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Visuao&#65533;"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Visuao&#65533;"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
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
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

And:
justin@justin-desktop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
justin@justin-desktop:~$ 

Well, IIRC i couldn't see the splash screen on my HDTV last night, but i read a post and put in some code and i could see it again. 

Also, i DON'T see the grub menu on my HDTV, i just memorized down 4x for when I use xp lol.

---

### Post by HoLLyw00dGT on 2008-03-03
Any idears? My monitor is cutting off my screen =(

---

### Post by erginemr on 2008-03-03
Give me a few hours. I will try to work it out...

---

### Post by erginemr on 2008-03-03
First a DISCLAIMER: 
I have never ever used a HDTV and connected it to my computer. So, if my suggestion breaks down your HDTV (which is unlikely, most probably it will shut itself down) do not blame me and hold me responsible for this. 

With that out of the way, I have used the following site to generate a new modeline for 1360x768@60 (also see the attachment):
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Add these two lines to your xorg.conf file, restart your X server with Ctrl+Alt+BackSpace and see what happens. Kindly note that you need to change two lines below:

```
Section "Monitor"
	Identifier	"Visuao "
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
 [color="red"] **modeline  "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807**[/color]
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Visuao "
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		[color="red"]**"1360x768@60"**[/color]  "1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
```

The following sites discuss the X configuration on similar hardware. You might want to take a look at them:

[http://www.neowin.net/forum/lofiversion/index.php/t598618.html](http://www.neowin.net/forum/lofiversion/index.php/t598618.html)
[http://suseforums.net/index.php?showtopic=29766](http://suseforums.net/index.php?showtopic=29766)
[http://www.linuxquestions.org/questions/linux-hardware-18/xorg.conf-and-lcd-tv-monitor-615532/](http://www.linuxquestions.org/questions/linux-hardware-18/xorg.conf-and-lcd-tv-monitor-615532/)
[http://sprinkleofcocoa.blogspot.com/2005/11/xorgconf-file-for-dual-headed-linux.html](http://sprinkleofcocoa.blogspot.com/2005/11/xorgconf-file-for-dual-headed-linux.html)
[http://www.besttechie.net/forums/configure-xorg-on-widescreen-tv-t7522.html](http://www.besttechie.net/forums/configure-xorg-on-widescreen-tv-t7522.html)

If the modeline I have given does not work, you may consider trying the modeline given in the 5th (last) link. Again, you will need to make changes in two lines.

Good Luck...

---

### Post by HoLLyw00dGT on 2008-03-03
> **erginemr said:**
> First a DISCLAIMER: 
I have never ever used a HDTV and connected it to my computer. So, if my suggestion breaks down your HDTV (which is unlikely, most probably it will shut itself down) do not blame me and hold me responsible for this. 

With that out of the way, I have used the following site to generate a new modeline for 1360x768@60 (also see the attachment):
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Add these two lines to your xorg.conf file, restart your X server with Ctrl+Alt+BackSpace and see what happens. Kindly note that you need to change two lines below:

```
Section "Monitor"
	Identifier	"Visuao "
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
 [color="red"] **modeline  "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807**[/color]
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Visuao "
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		[color="red"]**"1360x768@60"**[/color]  "1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
```

The following sites discuss the X configuration on similar hardware. You might want to take a look at them:

[http://www.neowin.net/forum/lofiversion/index.php/t598618.html](http://www.neowin.net/forum/lofiversion/index.php/t598618.html)
[http://suseforums.net/index.php?showtopic=29766](http://suseforums.net/index.php?showtopic=29766)
[http://www.linuxquestions.org/questions/linux-hardware-18/xorg.conf-and-lcd-tv-monitor-615532/](http://www.linuxquestions.org/questions/linux-hardware-18/xorg.conf-and-lcd-tv-monitor-615532/)
[http://sprinkleofcocoa.blogspot.com/2005/11/xorgconf-file-for-dual-headed-linux.html](http://sprinkleofcocoa.blogspot.com/2005/11/xorgconf-file-for-dual-headed-linux.html)
[http://www.besttechie.net/forums/configure-xorg-on-widescreen-tv-t7522.html](http://www.besttechie.net/forums/configure-xorg-on-widescreen-tv-t7522.html)

If the modeline I have given does not work, you may consider trying the modeline given in the 5th (last) link. Again, you will need to make changes in two lines.

Good Luck...
Wow man, you really didn't need to put that much effort into it...i really really appreciate it. I'll have to wait till this evening to try it though as I have to leave for class all damn day.

-Justin

---

### Post by HoLLyw00dGT on 2008-03-03
Ok, well i added those 2 lines, although they didn't line up perfectly like the picture shouldn't they still work? Also, i'm not exactly sure what that did. How do i even select the 1360x768 resolution? 

I just dont understand this, why wouldn't they just HAVE a freaking setting for this. I'm so close to just deleted my Linux partition =( I can't even get my resolution to work =( my login screen is as wide as my monitor, but after i log in it moves to whatever default is. I mean seriously...even if you select 1360x768 monitor on the "Screens and graphics" program there isn't even a selection FOR 1360 x 768...ignorant.

EDIT* Seems as if my box for my TV says 1366 x 768...could THIS be an issue? My XP has 2 TINY black bars on each side of the screen but nothing is cut off.

-Justin

---

### Post by erginemr on 2008-03-03
So, I understand that adding 1360x768 has had no effect whatsoever in the screen view. That is, it still shows as 1024x768 before. Is this correct?

Did you also try the lines given in the 5th link above?

P.S. I first tried 1368x768, but the modeline generator has changed it deliberately to 1360x768. So, I thought given that your Windows system also uses this resolution, maybe this is the way to go.

---

### Post by erginemr on 2008-03-04
Unfortunately, "Screens and Resolutions" is buggy. It reports your refresh rate (55 Hz) wrong, and sometimes, misconfigures your xorg.conf file if you allow to do it.

I still have a few more tricks: 

1. First things first, take a copy of your current config file, to be restored if we mess things up:
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

2. As a standard procedure, open the same file with root permissions:
```
gksudo gedit /etc/X11/xorg.conf
```

First add this line, comment out (#) the one with "nv", save and exit, and restart your X server (Ctrl+Alt+BackSpace):

```
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
**[COLOR="Red"]	# Boardname	"nv"[/COLOR]**
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
**[COLOR="Red"]        Option          "MetaModes" "1360x768@60"[/COLOR]**
	Screen	0
EndSection
EndSection
```

3. If the one above does not do anything, then add this line instead:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Visuao "
	Defaultdepth	24
	SubSection "Display"
		Depth	24
**[COLOR="Red"]		Virtual	1360	768[/COLOR]**
		Modes		"1360x768@60"  "1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
```

Gotcha! Bull's Eye! We should have deleted this line for God's sake:
```
Virtual	1024	768
```
[B]FORGET ABOUT ANYTHING ELSE, DELETE THIS LINE ONLY AND SEE WHAT HAPPENS!
[/B]
4. Final trick if none of the above works is to reconfigure the xorg.conf file (when the computer is started as connected to the HDTV) with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then post the new xorg.conf here and we shall further work on the resulting file.

But I strongly believe (hell, I am sure) that deleting the line Virtual above will put and end to your troubles.

---

### Post by HoLLyw00dGT on 2008-03-04
```
Section "Files"
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
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Visuao&#65533;"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    modeline  "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Visuao&#65533;"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
                Virtual 1360     768
		Modes		"1360x768@60"   "1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
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
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

Well all I did was delete that virtual line, IDK what to do after that, but i know that after i restarted it didn't do anything. I'm still in 1360 x 768 LCD with 800x600 res. Did i do that right?

***EDIT*** I can select 1360 x 768 res when i choose 1360 x 768 LCD now, but it says no signal when i apply. Also, my login screen says no signal. plus it only gives me options of 50hz not 60 =(

---

### Post by HoLLyw00dGT on 2008-03-04
Along with that edit:

LATEST XORG:

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

Section "Files"
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
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Visuao&#65533;"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Visuao&#65533;"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
                Virtual 1360    768
		Modes		"1360x768@60"   "1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
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
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by erginemr on 2008-03-04
Gosh! :(

If you are still with me, try the 1st item (backup your current config file) and 4th item (reconfigure your config file from the terminal) from my previous post all the while having HDTV connected. 

But use:
```
sudo dpkg-reconfigure xserver-xorg
```
instead (without a "-phigh" parameter) which will ask you a couple of questions including the desired screen resolutions. You may refer to your current xorg.conf file above to answer some of the more technical questions of the installer.

Restart your X server, see what happens and post back the outcome with a listing of the new xorg.conf file.

---

### Post by HoLLyw00dGT on 2008-03-04
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

Section "Files"
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
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync

	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes	        "1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
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
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

Well, now i have a huge black stripe across my screen and I can't scroll down very far on webpages...even though i can see my kiba dock on the black stripe.

---

### Post by xc3RnbFO8P on 2008-03-04
Do you have DVI>HDMI connection?
Have you tried Nvidia settings?

---

### Post by HoLLyw00dGT on 2008-03-04
Vid card has dvi, came with dvi to vga adapter. TV is thus hooked up vga to vga. IDK how to mess with nvidia settings.

---

### Post by lswest on 2008-03-04
you can install nvidia settings with ```
sudo aptitude install nvidia-settings
``` which is pretty much the Nvidia Control Panel for Linux ^^  then you can run it from a terminal with ```
nvidia-settings
```

---

### Post by HoLLyw00dGT on 2008-03-04
```
justin@justin-desktop:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

justin@justin-desktop:~$ 

```

All i get is a menu that i can uncheck boxes with...

---

### Post by mgranet on 2008-03-04
You need to run
```
sudo nvidia-settings
```

---

### Post by erginemr on 2008-03-04
Also in your current xorg.conf file, there is a line:
```
	Driver		"nv"
```
which means you have selected "nv" as the driver when you run:
```
sudo dpkg-reconfigure xserver-xorg
```

You should have selected "nvidia". Please do it again, but select "nvidia" this time.

Also, I advise you to shut off kiba-dock and Compiz Fusion until the end of this problem. The black line you see is probably because of kiba-dock, as it needs a compositing environment (Compiz-Fusion) to run. But since you are using "nv", there is no 3D and such glitches can be expected.

---

### Post by HoLLyw00dGT on 2008-03-04
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

Section "Files"
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
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Westinghouse"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Westinghouse"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
``` 

EDIT** [http://img166.imageshack.us/my.php?image=screenshotnvidiaxserverir2.png](http://img166.imageshack.us/my.php?image=screenshotnvidiaxserverir2.png)

^ is a screen shot up my nvidia settings box, it says CRT =(

Now what do ya think? Should i now go back and try the options listed before erginemr?

-Justin

---

### Post by erginemr on 2008-03-05
At least, the config file has recognized your HDTV monitor:
```
Monitor		"Westinghouse"
```
[http://www.xpcgear.com/ltv32w3.html](http://www.xpcgear.com/ltv32w3.html)

So, I believe we are on the right path. Don't worry about the nvidia-settings reporting as CRT.

Could you please try to force the system to 1360x768 with the following changes:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Westinghouse"
	DefaultDepth	24
	SubSection "Display"
		Modes		**[COLOR="Red"]"1360x768"[/COLOR]** "1024x768" "800x600" "640x480"
	EndSubSection
```

```
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
**[COLOR="Red"]        Option          "MetaModes" "1360x768"[/COLOR]**
EndSection
```

If this doesn't work, you can try enforcing 1360x768 by the drop-down menu of the nvidia-settings tool, if you have it as an option. Otherwise, I will get off your back. ;)

---

### Post by HoLLyw00dGT on 2008-03-05
Well I actually typed that in "westinghouse" There wasn't a westinghouse choice. Well, hey, i appreciate that last few days worth of work you have put in for me. Thanks a whole hell of a lot. I like the idea of linux and the fancy effects, but looks like it just wasn't for me. I won't use it unless i can use it on my big *** monitor :wink: Oh well, back to XP (couldn't leave it anyway) So here goes, how do i uninstall my linux partition? And when i do how do i use that unallocated space for my NTFS? (windows)

-Justin

---

### Post by xc3RnbFO8P on 2008-03-05
I think tou should try DVI>HDMI cable works better with Nvidia settings (has notthing to do with xorg.conf), and you get better quality.

---

### Post by erginemr on 2008-03-05
> **HoLLyw00dGT said:**
> Well I actually typed that in "westinghouse" There wasn't a westinghouse choice. Well, hey, i appreciate that last few days worth of work you have put in for me. Thanks a whole hell of a lot. I like the idea of linux and the fancy effects, but looks like it just wasn't for me. I won't use it unless i can use it on my big *** monitor :wink: Oh well, back to XP (couldn't leave it anyway) So here goes, how do i uninstall my linux partition? And when i do how do i use that unallocated space for my NTFS? (windows)

-Justin

OK Justin, if this is your decision... :(

But this thread has outlived its purpose, and since it has been marked with [SOLVED] not many people will come by and post here any more.

I have an idea on how to uninstall Ubuntu, but I also want other knowledgeable people come up perhaps with a better idea contribute to the solution. So, I suggest you to start a new thread with a title "Uninstalling Ubuntu" or similar, and give a link to it here, so that I can also follow and post there. 

Or better still, you can do a search in the forum and find an answer without posting at all, as I know, quite a few other people (alas...) wanted to uninstall Ubuntu and append its partition to their existing Windows partition.

You are most welcome. I am sorry that Ubuntu didn't work for you, but maybe it will a year from now, so don't forget to follow its progress. 

Take care yourself,

Emrah

---

