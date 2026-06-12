---
title: "Login resolution help"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by FNDII on 2007-07-12
When I turn on the computer the log on screen is at the wrong resolution, is there a way to change it?

---

### Post by southernman on 2007-07-12
Is this a fresh install or did you add a new video card to your system?

The only way *I* know of to fix it would be...

> sudo dpkg-reconfigure xserver-xorg

You can see the changes after rebooting

---

### Post by FNDII on 2007-07-12
Its a fresh install, new linux/ubuntu user. My desktop resolution is fine, just the login screen. 

and i remember having and awful time with that command and all its questions

sudo dpkg-reconfigure xserver-xorg

Is the another way to change the login screen resolution?

---

### Post by southernman on 2007-07-12
Surely there is, but it's beyond my knowledge.

---

### Post by southernman on 2007-07-12
Have a look at these two links... may help you out:

[https://wiki.ubuntu.com/USplash/view]("https://wiki.ubuntu.com/USplash/view")

[http://ubuntuforums.org/showthread.php?t=29289]("http://ubuntuforums.org/showthread.php?t=29289")

---

### Post by bodhi.zazen on 2007-07-12
OK, first, to reconfigure X the easy way use :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The -phigh flag will select defaults for everything but resolution (makes it much easier if ou ar not familiar with all the options :) )

OK , next , grub ...

First try editing xorg.conf :

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```

You are looking for the "screen section"


Section "Screen"

Look for the default depth : DefaultDepth    24

Then in the corect subsection :

        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768"
        EndSubSection

GRUB will use the very 1st resolution listed on the "Modes" Line, so change it to your desired resolution.

Save your changes and log out. Re-start GDM (hit Ctrl-Alt-Backspace at the GDM login screen).

If you are still having problems you may need to set your framebuffer. This is easy to do, but see here for details :

[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

---

### Post by Wim Sturkenboom on 2007-07-12
From the first post given in the second link above ( [http://ubuntuforums.org/showthread.php?t=29289](http://ubuntuforums.org/showthread.php?t=29289) )
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"A90f"
	**DefaultDepth	24**
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		**Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"**
	EndSubSection
EndSection
```

It shows the resolutions that the system can use for each depth. When X starts, it checks the defaultdepth (24 in the example) and next tries the resolutions(specified for that depth from left to right till it finds one that is valid, So it will try 1600x1200 first, next 1280x1024 etc. So if 1600x1200 is possible, it will use that and that is what you get with the login screen. After login, gnome, kde etc will use what you have specified.

If you move the desired resolution to the beginning of the line, X will use that (if it's valid).

PS This is my understanding how it works. I don't have Ubuntu at hand at the moment so can't verify.

---

### Post by icecruncher on 2007-07-12
the only thing really necessary is the 
```
sudo dpkg-reconfigure xserver-xorg
```
that should do it.
did it for me

---

### Post by FNDII on 2007-07-12
I have tried these ways a couple times now, none seem to help. I want my login screen to be at 1360x768 (thats whats the manual says). In most of those options i never saw my resolution.

---

### Post by annda on 2007-07-12
this is a very strange resolution...

however, if you want that, follow bodhi's advice and make sure the highest you have in your xorg.conf is 1360x768.

UPDATE: maybe i wasn't clear at first - delete anything higher than your desired resolution and put yours first.

---

### Post by FNDII on 2007-07-12
Okso following the directions given, when i get to this screen 

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"A90f"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection




I should change this part

SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

To what in order to make my login screen resolution to display at 1360x768 (thats whats the manual says)?

btw it is a funny resolution, Ubuntu has that resolution already for me in the desktop, I didnt have to do anything is was preset.

---

### Post by bodhi.zazen on 2007-07-12
If that resolution is working, change it to ....

SubSection "Display"
Depth 24
Modes "1360x768" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

---

### Post by cogadh on 2007-07-12
Are you 100% sure that is the actual resolution you are using? If we are looking at your current xorg.conf file, that resolution isn't listed in it. Without that resolution in the xorg.conf file, I don't think there is any way that your monitor will actually display at that resolution.

If that monitor identifier in your xorg.conf indicates that you are using a Viewsonic A90f+ 19" monitor, it is not even capable of doing that resolution. The top resolutions for that monitor are:
1792x1344 @ 61Hz
1600x1200 @ 68Hz
1280x1024 @ 80Hz
1152x870 @ 94Hz
1024x768 @ 105Hz
800x600 @ 132Hz

It might be helpful if you posted the Monitor section of the xorg.conf, it may explain what is going on

---

### Post by FNDII on 2007-07-12
I have I 31' westing house LCD

whats the best way to open my  xorg.conf file?

---

### Post by FNDII on 2007-07-12
Got It, I think?


Section "Monitor"
	Identifier	"LTV-32w1"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

---

### Post by cogadh on 2007-07-12
First create a duplicate of your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then open it for editing like this:
```
sudo gedit /etc/X11/xorg.conf
```
If you use KDE, do this instead:
```
sudo kate /etc/X11/xorg.conf
```

---

### Post by FNDII on 2007-07-13
Its hard to hit the bottom left hand icon at the log on screen ><

Nothing seems to work

---

### Post by cogadh on 2007-07-13
You seem to have two different monitors configured in your xorg.conf (technically, one of them must be an ATI driver configure function). In your xorg.conf, what does it say for the Monitor entry under the Screen section?

---

### Post by FNDII on 2007-07-13
I know its unsightly but I'll just post the whole thing, maybe you can see some other error.




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

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
	Load    	"dbe"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Identifier	"LTV-32w1"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:4:0:0"
EndSection

Section "Device"
	Identifier  	"aticonfig-Device[0]"
	Driver      	"fglrx"
	Option      	"Capabilities" "0x00000800"
	Option      	"UseFastTLS" "off"
	Option      	"KernelModuleParm" "locked-userpages=0"
 EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 (PCIE)]"
	Monitor		"LTV-32w1"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes "1360x768" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by cogadh on 2007-07-13
I'm afraid this may be really beyond me. I've never seen an xorg.conf with two different Monitor, Device and Screen entries like that, except when there are actually two different video cards and monitors connected. I think the entries that are actually being used are the second entries for each, but I can't be certain. Someone else who is more familiar with the ATI driver configuration may be able to offer more help.

---

### Post by bodhi.zazen on 2007-07-13
> **cogadh said:**
> I'm afraid this may be really beyond me. I've never seen an xorg.conf with two different Monitor, Device and Screen entries like that, except when there are actually two different video cards and monitors connected. I think the entries that are actually being used are the second entries for each, but I can't be certain. Someone else who is more familiar with the ATI driver configuration may be able to offer more help.

cogadh: You might be interested in the following information.

You can have as many devices defined in xorg.conf as you like, as long as each is functioning.

You then outlay them in the server section, you can for example have two keyboards and two mice, two video cards, etc.

See this thread for an example :

[http://ubuntuforums.org/showthread.php?t=240150](http://ubuntuforums.org/showthread.php?t=240150)

The specifics of these options are beyond this thread, but it not all that different for what you are used to looking at ;)


FNDII : I am sorry but I do not have time at the moment to sort out your xorg.conf. Take a look at the above link to see if it helps you at all.

If you need help, are you running dual monitors on dual video cards or what ?

---

### Post by cogadh on 2007-07-13
I was already well aware that you can have multiple devices configured, but why would you have multiple devices configured if you don't have multiple devices connected? FNDII already said he only had his 32" LCD connected, not multiple monitors. If he does have multiple monitors, then his xorg.conf does make a lot more sense to me. 

I've still never really dealt with the intricacies of the ATI driver config before so I still don't think I can properly assist with this issue.

---

### Post by FNDII on 2007-07-13
Tried this fix as well, from Wiki. Whenever I try to mess with the login screen resolution I always get the same error. The error come from the monitor, "signal out of range". I can log in through the black screen and Ubuntu will load up, so I can change it back.

 How to enable Large Widescreen Support

    * 24/23" widescreen monitors sometimes have issues running 1920x1200.
    * Examples include: Dell 2405, HP 2335 or an Apple Cinema Display. 

sudo gedit /etc/X11/xorg.conf

    * CAUTION: Feisty has something called Desktop Effects which can reconfigure your xorg.conf file automatically. If you manually edit the file Desktop Effects may not work properly. (Always make a copy of the xorg.conf file before editing. cp /etc/X11/xorg.conf /etc/X11/xorg.conf.A) 

    * Add the following line to the appropriate "Monitor" section 

Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235

    * For example the HP2335 should now look like: 

Section "Monitor"
	Identifier	"hp L2335"
	Option		"DPMS"
	Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

---

### Post by bodhi.zazen on 2007-07-13
> **cogadh said:**
> I was already well aware that you can have multiple devices configured, but why would you have multiple devices configured if you don't have multiple devices connected? FNDII already said he only had his 32" LCD connected, not multiple monitors. If he does have multiple monitors, then his xorg.conf does make a lot more sense to me. 

I've still never really dealt with the intricacies of the ATI driver config before so I still don't think I can properly assist with this issue.

Ah, cool, I see you are ahead of me then :)

I do not understand FNDII's exact configuration either :(

---

### Post by FNDII on 2007-07-13
could i have made an extra one by accident?

I picked this one from the options in "sudo dpkg-reconfigure -phigh xserver-xorg"

Section "Monitor"
Identifier "LTV-32w1"
Option "DPMS"
EndSection


I did not pick the other one if must have auto picked it

Section "Monitor"
Identifier "aticonfig-Monitor[0]"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection




I was thinking maybe I should delete one of them< bit information from the both of them are used in 

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc R430 [Radeon X800 (PCIE)]"
Monitor "LTV-32w1"
Defaultdepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1360x768" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection



Now i'm thinking I should merge them somehow?

---

### Post by FNDII on 2007-07-13
Ok so i was messing around and screwed everything up. 

Ran "sudo dpkg-reconfigure -p high xserver-xorg" from Generic mode.

Also re-ran the ati x800 series fix (bc i think i had to?)

When I booted back up the log in screen was as the usual messed up resolution. and it was also messed up on my desktop. The tool bars are off the screen. I managed to click on system and get to screen resolution.

It was set at 1920x1080 i changed it back to what my manual tells me to 1360x768. I know that is a funny resolution, but Ubuntu has it as an option. Also World of Warcraft has a special 1360x768(wide) option for resolution.

So I guess the default resolution that Ubuntu picks for me it 1920x1080 and i need 1360x768.

Funny thing is i don't even see 1920x1080 as an option in the xorg.conf

Its really frustrating feels like I'm out of options.:(

---

### Post by southernman on 2007-07-13
> **FNDII said:**
> Tried this fix as well, from Wiki. Whenever I try to mess with the login screen resolution I always get the same error. The error come from the monitor, "signal out of range". I can log in through the black screen and Ubuntu will load up, so I can change it back.

 How to enable Large Widescreen Support

    * 24/23" widescreen monitors sometimes have issues running 1920x1200.
    * Examples include: Dell 2405, HP 2335 or an Apple Cinema Display. 

sudo gedit /etc/X11/xorg.conf

    * CAUTION: Feisty has something called Desktop Effects which can reconfigure your xorg.conf file automatically. If you manually edit the file Desktop Effects may not work properly. (Always make a copy of the xorg.conf file before editing. cp /etc/X11/xorg.conf /etc/X11/xorg.conf.A) 

    * Add the following line to the appropriate "Monitor" section 

Modeline    "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235

    * For example the HP2335 should now look like: 

Section "Monitor"
    Identifier    "hp L2335"
    Option        "DPMS"
    Modeline    "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

You may be mistaken here. By that I mean in the quoted copy above notice this line below:

>      * Add the following line to the appropriate "Monitor" section 

Modeline    "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235The key word here is *Add* not *Replace*

I think this section should read as follows:

> Section "Monitor"
    Identifier    "hp L2335"
    Option        "DPMS"
     Modes "1360x768" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    Modeline    "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSectionIt seems though, if you don't want to use that resolution (1920x1200) then there would be no point in worrying with this part. Frankly, I don't know... TBH.

Then again, I am just guessing (read: grasping at straws) in order to try and help you (and the other two guys) finger this one out.

*Edited - Your not out of options here - just haven't found the right one for your specific situation is all. Tough times build character! ;)

*Edit #2 - Here is my xorg.conf (pertinent sections only)

> Section "Device"
    Identifier    "ATI Technologies Inc R480 [Radeon X850Pro]"
    Driver        "ati"
    BusID        "PCI:2:0:0"
    VideoRam    262144
EndSection

Section "Monitor"
    Identifier    "MX75"
    Option        "DPMS"
    HorizSync    30-65
    VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc R480 [Radeon X850Pro]"
    Monitor        "MX75"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by FNDII on 2007-07-13
Where does the computer get 1920x1080 resolution in the first place (thats the resolution of the login screen. That resolution is not even in the xorg file.

If I find that out maybe it would help.

---

### Post by southernman on 2007-07-13
Maybe your monitor supports it. If you "really" want to know, go to the manufactures website and look for the specs or your monitor... including horizontal and vertical refresh rates. I noticed earlier your xorg.conf doesn't list them.

Knowing this info, and doing a full on sudo dpkg-reconfigure xserver-xorg command, you can manually enter these res and ref rates.

---

### Post by FNDII on 2007-07-14
Login is the first thing I see when i boot up and its all distorted all the time!!

It takes to long to find that change session button in the bottom left hand corner. Because I have to find it!!

I have tried every fix that i could find. Some one else has had to have had a problem like mine.

---

### Post by Wim Sturkenboom on 2007-07-14
From the user manual that I downloaded ([http://www.hdtvsolutions.com/pdf/westman.pdf](http://www.hdtvsolutions.com/pdf/westman.pdf)), page 24
> 
PC compatible:
recommended:
**1280x720@75Hz**
supported:
1280x1024@60Hz
1280x1024@75Hz
1280x768@60Hz
1024x768@60Hz
1024x768@75Hz
**832x624@75Hz**
800x600@60Hz
800x600@75Hz
720x400@70Hz
640x480@60Hz
640x480@75Hz
So the resolution that you mentioned is not supported so I'm not really surprised that you get 'out of range' errors from your TV.

Widescreen TVs have an aspect ratio of 16:9. Only the bold resolutions match this ratio and will not distort your picture.

---

### Post by FNDII on 2007-07-14
A four page thread for login resolution, :(

I dont think i have any other options, just chalk this up to bad ati drivers.

---

### Post by FNDII on 2007-07-16
one day bump

---

### Post by pandion on 2007-07-23
Hi,

I'm both new to the forum and to Ubuntu (& Kubuntu/Xubuntu), and ran into the same login screen resolution annoyance in both Ubuntu and Kubuntu (I am not however new to computers, hardware and various operating systems).  The image on the login screen would be too large to show the option buttons etc., but they could be accessed by moving the mouse around which causes the image to move.  From what I have read (as already stated in other posts), the first resolution listed in XORG.CONF for your Screen is the one used on the login screen.  I have found that this does not seem to be the case.  It looks like it uses the highest resolution that is listed or available for your Screen.  This is a configuration issue and not a video driver issue.

I have however found a fix that is both simple and works.  Edit the XORG.CONF file and find the Section "Screen".  This section should include your Default Screen, Device (video adapter) and Monitor that is being used and the Default Depth.  Below this is a Subsection "Display".  Find the line that says "virtual" (this is not in quotes in XORG.CONF) followed by a display resolution.  In the case of my PC, this was "virtual 1280 1024" (not in quotes).  1280x1024 is the highest resolution listed in XORG.CONF supported by my monitor, and this appears to be the resolution the login screen uses.  Since I am running my desktop at 1024x768, I changed this line to read virtual 1024 768.  Now my login greeter screen displays at 1024x768 and the image fits properly.  I confirmed this by changing the login greeter image to a 1024x768 image file (png, jpg, etc.), and the image displays correctly.  If I use the same image as my desktop background, I can see that it's size does not change.  Just edit the "virtual" line and change the resolution to the resolution that you use for your greeter image (I like to use the same resolution as the desktop) and it will be displayed correctly.

---

### Post by FNDII on 2007-07-23
My login screen resolution is not listed in my xorg file. As best I can tell my login resolution is 1920x1080. The highest listed in the xorg file is 1280x1024. 

My problem is still the same as yours though. Buttons ect are off the screen and i have to move the mouse around in order to hit the buttons.

Also I do not see a virtual line in my xorg

There were Questions about my strange resolutions settings. It says "recommended 1360x768" in the manual. When I have this monitor hooked up That resolution option appears un the Ubuntu Settings and also World Of Warcraft. 

Is 1360x768 even an option for you?

---

### Post by pandion on 2007-07-25
I did a little checking based on the XORG.CONF you posted earlier.  Based on that, if I understand correctly you're using a Westinghouse 32" LCD TV LTV-32w1 as your Monitor, and it's the only Monitor you're using (unless this is a laptop/notebook PC and you're not always connected to the LTV-32w1?).  Your PC has an ATI Radeon X800 PCIe Video Adapter (not sure if this model is the exact name, but it looks like it supports dual displays and TV out, which might explain the two monitors and two screens).  The resolution that you want to use must be supported by both the Monitor and the Video Adapter.  1360x768 is not listed as a supported resolution (unless it's a typo error) by the LTV-32w1.  The LTV-32w1 does support 1366x768 (1366 seems strange since it's not a multiple of 8 or 16, but that's what it says.  I'm guessing this could be an error on the website, so double check your desktop resolution and the manual) as it's native and maximum resolution when connected to a PC.  According to the XORG.CONF link I posted below, is is possible to switch to the next mode (cycle through the supported resolution modes) with Ctrl+Alt+Keypad-Plus and to the previous mode with Ctrl+Alt+Keypad-Minus, which might be a quick way to at least see what you're doing during login (I have tried this and it doesn't seem to work for me).  Before you can fix the login greeter resolution, you need to have the desktop resolution working.  Then try to match the login greeter resolution to be the same as your desktop.

LCD TV LTV-32w1 Specs:
[http://www.westinghousedigital.com/details.aspx?itemnum=15](http://www.westinghousedigital.com/details.aspx?itemnum=15)

ATI Radeon X800 Specs:
[http://ati.amd.com/products/radeonx800/specs.html](http://ati.amd.com/products/radeonx800/specs.html)
(this may not list all of the supported resolution modes, but they may be in the manual if you have it)

XORG.CONF Info (this is a good reference):
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

By your XORG. CONF, it looks like you're actually using these sections (also looks like two Screens and two Monitors are defined, and the Default Screen section is not currently being referenced in the ServerLayout).  The ServerLayout is the highest level and specifies what's actually being used and binds them all together, and the Screen section binds the Video Adapter and the Monitor together.

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0   (references the unique name given to the Screen being used)
  Inputdevice "Generic Keyboard"
  Inputdevice "Configured Mouse"
  Inputdevice "stylus" "SendCoreEvents"
  Inputdevice "cursor" "SendCoreEvents"
  Inputdevice "eraser" "SendCoreEvents"
EndSection

Section "Screen"
  Identifier "aticonfig-Screen[0]"     (matches reference in ServerLayout for Screen 0)
  Device "aticonfig-Device[0]"         (references unique name of Video Adapter Device)
  Monitor "aticonfig-Monitor[0]"       (references unique name of Monitor)
  Defaultdepth 24
  SubSection "Display"
    Viewport 0 0
    Depth 24
    virtual 1360 768          (*If you try the "virtual" setting, this is the syntax and location)
  EndSubSection
EndSection

     (*You can also try adding it to the Default Screen section right after Depth 24, or for each Depth) 

Section "Device"
  Identifier "aticonfig-Device[0]"     (matches reference in Screen for Video Adapter Device)
  Driver "fglrx"
  Option "Capabilities" "0x00000800"
  Option "UseFastTLS" "off"
  Option "KernelModuleParm" "locked-userpages=0"
EndSection

Section "Monitor"
  Identifier "aticonfig-Monitor[0]"                     (matches reference in Screen for Monitor)
  Option "VendorName" "ATI Proprietary Driver"
  Option "ModelName" "Generic Autodetecting Monitor"
  Option "DPMS" "true"
EndSection

As long as you have a backup copy of your XORG.CONF it should be safe to try adding the "virtual 1360 768" line.  Worst case, you can always boot with a live CD and put the backup copy back if it doesn't work.  The "virtual" line specifies the maximum resolution that will be accepted, resolutions that are higher/larger than this setting will be rejected.  This setting will also affect the desktop resolution.  For example, I tested changing mine to "virtual 640 480", which resulted in the login greeter being displayed at 640x480 as well as the desktop, even though the desktop is configured for 1024x768.  Read the section in the XORG.CONF manual (I posted the link above) regarding this setting (not all hardware supports it, but I'm guessing yours does).

Hope this helps!

---

### Post by FNDII on 2007-07-25
On lunch no time to make those changes.

the keypad +/- worked for  me it does help.

not sure if its worth noting but in  beryl the resolution is fine but all the text is at what looks to be the login resolution.

---

### Post by rhaleblian on 2007-07-25
Thanks, using Virtual in my 24-bit Display subsection did adjust the login screen resolution. I'm running "Dapper" insude VMWare Player, inside Windows XP.

---

### Post by rhaleblian on 2007-07-25
Oops, just realized - using Virtual restricted the maximum available resolution when logged in. In my case,

Virtual 800 600

Only allows 800x600 and 640x480. The user should be able to choose any device supported resolution; we just want to specify the login screen resolution separately, from available modes, eg

DefaultMode "800x600"

however in the xorg.conf manpage i see nothing like DefaultMode.

---

