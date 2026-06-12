---
title: "How to edit conf and similar files in console?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by sa_ill on 2007-06-30
I know its a noob question, but I just cant edit these files.
I basically want to edit my xorg.conf
when i type sudo vim /etc/X11/xorg.conf
i get the contents in the file, the problem is i cant type anything, even backspace doesnt work
Delete key works to erase text but thats it, if I press shift or anything like that something funny happens

help

---

### Post by reset3x on 2007-06-30
try sudo gedit...

---

### Post by avik on 2007-06-30
> **sa_ill said:**
> I know its a noob question, but I just cant edit these files.
I basically want to edit my xorg.conf
when i type sudo vim /etc/X11/xorg.conf
i get the contents in the file, the problem is i cant type anything, even backspace doesnt work
Delete key works to erase text but thats it, if I press shift or anything like that something funny happens

help

Yeah, vim is hard to learn.  It's worth it, though I haven't taken the time to learn it yet.

Like reset3x said, sudo gedit *<filename>* will work.  Another option is sudo nano *<filename>* which is a command line editor, like vim, but very simple to use.

---

### Post by eternalsword on 2007-06-30
for the console, you probably want nano

nano -w /path/to/file

the -w flag is so that long lines don't automatically break.

within nano to exit press Ctrl+x
if you haven't made any changes to the file it will just exit
if you have made any changes, it will prompt if you want to save the changes at which point typing n will exit without saving and typing y will then prompt you where you want to save it so just hit Enter to save the file you opened.

before opening xorg.conf, or any system files for that matter, it's always advisable to make a backup
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak.`date +%Y%m%d`
will give you a backup for the current date eg xorg.conf.bak.20070630 if you did it today

hope that helps you

---

### Post by reset3x on 2007-06-30
> **eternalsword said:**
> for the console, you probably want nano

nano -w /path/to/file

the -w flag is so that long lines don't automatically break.

within nano to exit press Ctrl+x
if you haven't made any changes to the file it will just exit
if you have made any changes, it will prompt if you want to save the changes at which point typing n will exit without saving and typing y will then prompt you where you want to save it so just hit Enter to save the file you opened.

before opening xorg.conf, or any system files for that matter, it's always advisable to make a backup
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak.`date +%Y%m%d`
will give you a backup for the current date eg xorg.conf.bak.20070630 if you did it today

hope that helps you

Hah!!! Good catch!!! Just came back to edit my post and tell him to back up... :oops:

---

### Post by djchandler on 2007-06-30
> **reset3x said:**
> try sudo gedit...

You can hit the key combination "alt-F2" to bring up a command line dialog box so you do not have to open the terminal window first. Then enter the above. I also like to copy the files to my home directory first, and edit them there before they get placed into the restricted-to-root directories. You can become su in nautilus by hitting the above combination and entering

gksu "nautilus"

which will also give you rights to change permissions on files as well and move them around more easily.  This I find helpful, but use with great care. It's easy to disable the x server, but not so easy if you haven't backed up the original somewhere accessible, and know how to get the known working xorg.conf back using the command line interface. I've learned that from tinkering with xorg.conf myself. You can still get su rights from the command line using sudo as suggested above. ;)

DJ

---

### Post by sa_ill on 2007-06-30
cheers got it thanks a ton!!!!!!!!
now tell me how to change my resolution to 1440 into 900, which is my native resolution. i still cant get it higher than 1024 into 768
heres my xorg.conf
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
	Option		"XkbLayout"	"us,in"
	Option		"XkbVariant"	","
	Option		"XkbOptions"	"grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
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
	Identifier	"nVidia Corporation GeForce Go 7700"
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
	Device		"nVidia Corporation GeForce Go 7700"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1440x900"      "1024x768"	"800x600"	"640x480"
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

### Post by reset3x on 2007-06-30
Back up your xorg.conf and add 1440x900 to the other depths like you have in Depth 1... Then save the file and exit your editor.. Hit ctrl-alt-bksp to restart x....

---

### Post by djchandler on 2007-06-30
Your monitor needs more definitions as well. There are a number of variables for describing your monitor, including its size in millimeters, its horizontal and vertical sync rate ranges, and more. I'll see if I can find the one I was using with my previous  computer to fully indicate your monitor's capabilities. As an example, here's the description of my 27" ViewSonic HDTV.

Section "Monitor"
DisplaySize	596 335
HorizSync	30-80
VertRefresh	60-75
Identifier	"N2751w"
Option		"DPMS"
VendorName	"ViewSonic"
EndSection

That may help get you the better resolutions you are looking for.

---

### Post by sa_ill on 2007-07-02
yeh ive done that
i can enable the resolution from nvidia-settings, but sometimes it works and most of the times its curropted and hangs
also when i restart the resolution is set back to 1024 into 768

---

### Post by Raineer on 2007-07-02
When you say "I've done that", you added the resolution to the rest of the depths?

---

### Post by sa_ill on 2007-07-02
i did add the resolution but the other stuff i cant figure out.....
i can change the resolution through nvidia-settings but my screen gets sort of curropted and i gotta restart

---

