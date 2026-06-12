---
title: "1440x900 Resolution"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by tregarton on 2006-07-06
Right then, Ive tried 3 times to change the display to 1440x900.  I've had to re-install Ubuntu 3 times due to messing it up!

The latest download doesn't enable me to download 915resolution files now.  It says can't find them.   

If someone can be kind enough to detail a step by step process for changing the resolution I would be VERY grateful.

Please remember I'm BRAND new to Linux and am felling VERY strupid at the moment.  All I want to do is change the res, and I don't think I'll need the forum again

Rob
P.S. Total time spent trying to change resolution now stands at 9hours 34minutes

---

### Post by raffytaffy on 2006-07-06
ok it looks to me like u have to change your xorg file. to do this open up a terminal..type in the following. sudo gedit /etc/X11/xorg.conf  (im guessing u use gedit as your text editor) once the window pops up..scroll down to the Section "Screen" itll look something like this :
Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV40M? [GeForce Go 6200]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 24
Modes "1680x1050" "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
As you can see..i have 1680x1050 as my biggest resolution..u can add whatever res you need...then save it and restart X by pressing Ctrl + alt + backspace...once restarted...go to system-preferance-screen resolution...and change it to what u need ...hope this works

---

### Post by wylfing on 2006-07-06
I have a 1440x900 resolution monitor as well, and I am working fine. Post your /etc/X11/xorg.conf here and I will try to help you fix it.

---

### Post by tregarton on 2006-07-06
Right, please find below my AMENDED xorg.conf file.  I tried changing the files with the "look" posted by RaffyTaffy and when I restarted X it went to a DOS looking screen!!!!  Here's my file.  Please can someone edited for a Acer AL1916W monitor with resolution of 1440x900 running on a DELL 5150 with onboard 950 graphics.  Many thanks inadvanced:

Section "Device"
	Identifier	"Intel Corporation 945G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1916W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Monitor		"Acer AL1916W"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1280x1024" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by PingunZ on 2006-07-06
As posted in another thread today ::

in console type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select you resolution wint the SPACE BAR and continue with enter
Once your back in the console do Ctrl + Alt + Backspace
and in your real terminal type  * startx *

Grtz PingunZ

---

### Post by MicroBlueChip on 2006-07-06
Hi Rob,

Phil here. I happened across the forums here as also learning the desktop side of Ubuntu for the first time.

That xorg.conf file looks fine. After you have modified and saved it. Press **Ctrl+Alt+Backspace** and you will return to the shell prompt i.e. (DOS style mode) simply log in **(if needed)** using your username and password and type **startx** to reload the desktop environment.

Regards
Phil.

---

### Post by wylfing on 2006-07-06
Sorry guys, but those solutions aren't going to fix his problem. The first suggestion might get him set up with the right 1440x900 resolution, but he's still going to have a messed-up screen.

**tregarton** - Do you see the line that says "Modes" "1440x900" underneath "Depth 24"? Take note of that.

1. Open a terminal and type this:
```
gksudo gedit /etc/X11/xorg.conf
```

2. For every line that starts with "Mode", add the part that says "1440x900".

3. Modify your "Monitor" section to look like this:
```
Section "Monitor"
    Identifier "Acer AL1916W"
    HorizSync       24.0 - 80.0
    VertRefresh     56.0 - 60.0
    Option "DPMS"
EndSection
```

4. Save and close the file.

5. Log out.

6. Press Ctrl+Alt+Backspace to restart X.

At this point you should at least see something reasonable on your screen. You might have to fiddle with your monitor's settings to make things look just right.

---

### Post by tregarton on 2006-07-06
Right, Thanks all for your advice.  Many thanks Phil (you fix enough of my computer problems during the day!!)  I've copied my NEW xorg.conf file.  Now I replaced ALL res with 1440x900 and I get a new res appear in the System menu of 1600 x 1200 and NO option for 1440x900.  Any ideas.  I notice the refresh rate is still 75Htz.  here's my file:
Section "Device"
	Identifier	"Intel Corporation 945G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier "Acer AL1916W"
    HorizSync       24.0 - 80.0
    VertRefresh     56.0 - 60.0
    Option "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Monitor		"Acer AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

---

### Post by wylfing on 2006-07-07
Although the Intel 950 can run at 75 Hz, your LCD screen cannot. It should be 60. Choose System > Preferences > Screen Resolution and try changing the refresh rate to 60. That may be sufficient to unlock the proper resolution.

If that doesn't work, you may need to add a custom modeline to your xorg.conf file. Put this line in your "Monitor" section:
```
Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
```

(Those are the exact specs I am using, as reported by xvidtune, so they should be safe for you. However, bad modelines can mess up your monitor, just so I warned you.)

If *that* doesn't work, you might have a BIOS issue. Try looking in your BIOS for video settings. Something might be limiting what you can do in there.

---

### Post by tregarton on 2006-07-07
Many thanks wylfing I'll have a go!  (thought I'd reply before adding the modeline just incase I cannot see anything!!!!!

---

### Post by tregarton on 2006-07-07
Right I've done all that's mentioned.  I still only get the 1600x1200 as a NEW option.  I've attached by xorg.conf file for you all to view.

Section "Monitor"
Identifier "Acer AL1916W"
HorizSync 24.0 - 80.0
VertRefresh 56.0 - 60.0
Option "DPMS"
Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Monitor		"Acer AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

---

### Post by wylfing on 2006-07-09
Please post the entire contents of your xorg.conf file. Even though it might seem like the other parts are irrelevant, they may not be. (Rather than make a new post, I suggest editing your last post.)

---

### Post by Tom Brokaw on 2006-07-09
Rant cut, new thread posted here:
[http://www.ubuntuforums.org/showthread.php?t=212212](http://www.ubuntuforums.org/showthread.php?t=212212)

---

### Post by xrchris on 2006-07-09
> **tregarton said:**
>  Please can someone edited for a Acer AL1916W monitor with resolution of 1440x900 running on a DELL 5150 with onboard 950 graphics.  


Are you using the Acer LCD screen connected up to a Dell Inspiron Notebook and therefore needing DUAL monitor support?

---

### Post by xrchris on 2006-07-09
> **Tom Brokaw said:**
> Hi, I'm not looking for the resolution this person posted about, but I can't get the resolution I want: 1280 x 1024.

I opened up my xorg file, and all the spots that corresponded already had my desired res in them.  So I saved it and hit Ctrl Alt Bkspce, and now the whole thing is busted.  I can't start xserver, i'm getting some "power connection error," I can't get into the GUI - wth do I do?

On a more critical note, why is this so hard?  Why can't it just detect my fricking resolution, or offer the one I want in preferences?  argh!  sorry, just extremely frustrated that this seemingly simple task is monumentally difficult and does not respong to suggested fixes, or else they are too difficult for me to implement, and how did it break anyway??????????????????????????????????????????????????????

Can you start your own thread and post what hardware you are using especially the type of graphics processor.

---

### Post by tregarton on 2006-07-09
Right then, Here's my entire xorg.conf file. This is the ORGINAL one as I made a change yesterday and got a Warning message and couldn't load the graphic side of things - So re-installed Ubuntu to make life easier! I hope someone notices SOMETHING wrong - It's like a foreign language to me!

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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Intel Corporation 945G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1916W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Monitor		"Acer AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

---

### Post by BrunchMonolith on 2006-07-09
Thought I would install Ubuntu 6.06 this morning. I have the AL1916W monitor also; Since it did not detect the 1440x900 screen res, I have been fiddling with the xorg.conf file. This "works" for me:

> Section "Monitor"
Identifier "Acer AL1916W"
HorizSync 30-82
Vertrefresh 56-76
Modeline "1440x900" 106.5 1440 1520 1672 1904 900 901 904 932 -HSync +VSync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R300 NE [Radeon 9500 Pro]"
	Monitor		"Acer AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Note that in the "Screen" section, Device should be the same as Identifier in the "Device" section.

Following this I rebooted, went to System > Preferences > Screen Resolution, and 1440x900 was listed there, so I selected it and it works. Sort of. The resolution works however my system now frequently crashes. Back to 1280x800, or more likely Windows, unless a solution can be found.

---

### Post by wylfing on 2006-07-09
**tregarton** - 

OK, it looks like a BIOS issue (I don't have this video chipset so it took me a while to catch on). Let's try this:

1. Open a terminal a type:
```
sudo apt-get install 915resolution
```

2. Then type this:
```
sudo gedit /etc/X11/xorg.conf
```

3. Modify the Modes lines to include "1440x900" as an option. There is no need to delete all the other options, just add this one.

4. Save the file and close it.

5. Log out and press Ctrl+Alt+Backspace to restart X.

---

### Post by Mrs Harris on 2006-07-13
Hey guys,

Just wanna say thanks for posting all your help... I'm no fully able to use my lovely widescreen monitor.

Thanks,
Mrs H

---

### Post by BrunchMonolith on 2006-10-28
I still have a silver Acer AL1916W, with a Radeon 9700 gfx card and I'm now running Edgy.

If you can get 1440x900 res working, and your system remains stable, great! However, in both Dapper and Edgy, manually editing xorg.conf with suggestions given at sites like [http://eccentric.cx/wordpress/?p=112]("http://eccentric.cx/wordpress/?p=112") or [http://cornell.wordpress.com/2006/03/16/more-widescreen-configuration/]("http://cornell.wordpress.com/2006/03/16/more-widescreen-configuration/")  seems to lead to frequent X server crashes for me. I'm unsure if this was specifically due to bad configuration of the monitor, or a bad driver for my Radeon 9700.

Having installed Edgy recently, I wanted to get 1440x900 working properly, so I initially tried manually editing xorg.conf, which allowed me to select 1440x900 res, however again X tended to lock up frequently.

Solution for me was to install the ATI fglrx driver, then reinitialise the X-server settings using *dpkg-reconfigure xserver-xorg*, making sure all the settings were correct. Specifically, I selected the new driver (fglrx), turned off the framebuffer driver, selected just a few video modes which I might use (1440x900, 1280x800, 1152x768, 1024x768, 800x600 (included last 3 to be safe), horizontal refresh rate 24-80, vertical refresh rate 56-60, and 24 bit colour.

This created me a nice new xorg.conf, and Edgy now runs rock solid.

---

