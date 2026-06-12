---
title: "Terminal Window Whiteout"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-12
Trying to move from Windoze to Ubuntu. I am frustrated with the difficulty of changing/fixing screen issues (whining, I know). I tried to set up a higher screen resolution using nvidia-settings, and it worked, however, now all the terminal windows come up as white boxes with no text in them. Have a nvidia 6200 card. What do I need to do about fixing that issue?

---

### Post by benhagerty on 2007-08-12
I had the same problem and I have the same card. Here is the thread [http://ubuntuforums.org/showthread.php?t=495128](http://ubuntuforums.org/showthread.php?t=495128)

---

### Post by mikex on 2007-08-12
Ugh.

Thanks, but all this typing/editing/ctrl+this+that, do it again, now go get xyz program and try that, restart ...

I realize all that is fine for you hackers, but can't somebody make a gui that just does the screen  settings for us moving from windoze? Why do I have to do all the fidgeting? Most of what I see is cool, but that last 5 % is a pain.

](*,)

---

### Post by scrooge_74 on 2007-08-12
Because is faster to do it in text.  To do a GUI somebody has to waste their time on it (maybe you could support someone to do it).

Follow the instructions and it should be easy.  In most cases when you had DOS or WIn95 you had to edit your config.sys or autoexec.bat to get things to work so I don't see the difference.

And if you take the time to learn the commands you will find how powerful is your new Linux system

---

### Post by mikex on 2007-08-12
> **scrooge_74 said:**
> Because is faster to do it in text.  To do a GUI somebody has to waste their time on it (maybe you could support someone to do it).


Thanks for the response, but do you all want windoze users like me to use Ubuntu or not? I don't care how fast it is, it's taken me all morning to play with the settings and still no terminal text, so why would I care if a GUI takes 5 minutes to use vs 30 seconds for text - it isn't in my priority list. Also, I see lots of GUIs already available in Ubuntu for all kinds of things, which is what led me to try it, so why is one more for graphics setting "wasting their time"? I don't follow the logic of that statement, given all the GUIs that are written for Ubuntu.

Added this line as suggested in the other thread referenced above, didn't fix the issue, any other ideas?

Option "AddARGBGLXVisuals" "True"

---

### Post by scrooge_74 on 2007-08-12
18 months ago I was one of those Windoze power users with basically no clue what so ever on how to do things.

In many cases there are not enough users that is needed to make a GUI for things that are easy enough to do. Taking the time to read stuff will help you avoid further problems and get things going much easier in the future

---

### Post by mikex on 2007-08-12
> **scrooge_74 said:**
> 18 months ago I was one of those Windoze power users with basically no clue what so ever on how to do things.

In many cases there are not enough users that is needed to make a GUI for things that are easy enough to do. Taking the time to read stuff will help you avoid further problems and get things going much easier in the future

I see.

At least one person tried to point me in the right direction. I don't see the value of basically telling someone joining a community for assistance "Search for the answer my son and when you are worthy, you will find the solution". I have searched and I haven't found this "easy" solution. If it is "easy enough to do" why not just tell me or not respond if you don't know. Is this the Ubuntu initiation ritual?

---

### Post by scrooge_74 on 2007-08-12
Sorry but you come hard on people complaining, some one gave you directions on how to solve your problem and then you complain again.

You don't even post what you dont understand or if you even followed the instructions, people can hold your hand and walk you true things, but you have to work on your manners not just complain that there is no GUI for things.

benhagerty instructions are pretty easy to follow he made them step by step, you would be off better just telling you can't follow instructions instead of complaining.

---

### Post by mikex on 2007-08-13
> **scrooge_74 said:**
> 
You don't even post what you dont understand or if you even followed the instructions, people can hold your hand and walk you true things, but you have to work on your manners not just complain that there is no GUI for things.

benhagerty instructions are pretty easy to follow he made them step by step, you would be off better just telling you can't follow instructions instead of complaining.



OK, lets try it your way.

I posted before I tried this:

Option "AddARGBGLXVisuals" "True"

I followed the instructions and it didn't fix the issue. Maybe I can't follow instructions. I hope my manners are acceptable. Does anyone have any suggestions that I can manually type into a file in Ubuntu to fix the original issue of the terminal window being pure white after changing resolutions. Is Ubuntu for people like me trying to move from windoze, or isn't it, that's what I was led to believe , and that's why I am trying it, and that's why I joined your community to get help. Perhaps I completely mis-understood what I was getting into? It's certainly possible.

---

### Post by bapoumba on 2007-08-13
Okay, everyone cool down please. I know how frustrating this can be. But remember that terminal commands are most of the time the easiest way to do things.

I moved the thread to the "Absolute Beginner Talk" support forum. Sorry I cannot help you with video cards.

---

### Post by scrooge_74 on 2007-08-13
Post what is in your xorg.conf file

I am not sure but try giving the extra space between ...Visual""True"  as per the instructions

Again post the content of the xorg.conf file or at least attach it so people can take a look at it

---

### Post by mikex on 2007-08-13
OK, thanks, I'll do it when I get off work. I would like to understand something else, does Ubuntu go out and get the latest nvidia driver automatically through it's update system?

---

### Post by quinnten83 on 2007-08-13
Only if they are in the repositories and you have the right repositories enabled.
I'm not very sure about this though.
Perhaps if you've installed through automatix that they will.

---

### Post by scrooge_74 on 2007-08-13
Automatix will do some of it, but a lot of people will advice you to stay away from automatix, it could hurt more than it helps.  It is better to enable the repositories.  7.04 will use restricted drivers if you tell the system to use them.

---

### Post by bapoumba on 2007-08-13
BTW, when posting your xorg.conf, please tell if you need 3D accel (the open source driver nv does not support it but is really easy to get running).

---

### Post by mikex on 2007-08-13
> **scrooge_74 said:**
> Post what is in your xorg.conf file

I am not sure but try giving the extra space between ...Visual""True"  as per the instructions

Again post the content of the xorg.conf file or at least attach it so people can take a look at it

Alright, here is the text I thought was supposed to fix the issue:

Option "AddARGBGLXVisuals" "True"

and here is my x file. I already put the above text in, but it did no good. Perhaps I placed it in the wrong section (I understood it was the screen section, which is where I had put it), so I took it back out. If you would suggest exactly where in the file to place the text, plus any other ideas on how to get the terminal screen to not be completely white, I would appreciate it.

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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
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
	Identifier	"nVidia Corporation NV44A [GeForce 6200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

