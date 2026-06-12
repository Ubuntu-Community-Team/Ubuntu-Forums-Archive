---
title: "touchpad problems"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by kbar78 on 2007-07-25
Hello, recent Linux convert here.  I'm running Feisty Fawn on a Toshiba Satellite M35X and I was wondering what the most effective way to configure my touchpad would be?  My biggest issue is that the vertical scroll is waaay to sensitive.

Thanks for the help! :)

---

### Post by be4truth on 2007-07-25
touchpad problems

---

### Post by be4truth on 2007-07-25
Synaptic TouchPad configuration tool
QSynaptics aims to help desktop users to configure their synaptics
touch pad that's commonly used in laptops. The program uses Qt 3.x,
is easy to manage and performs the basic configuration steps to use
your pad more efficiently. The program is based on the X11 synaptics
touch pad driver.


Open a shell and paste this into it:

```
sudo apt-get install qsynaptics
```

You will find this utility in the program utility menu

---

### Post by anewguy on 2007-07-25
I think when you do that you also need to add 

Option   "SHMConfig"  "true"

to the touchpad section in xorg.conf, don't you?? (I know you do in order to use gsynaptics).:)

---

### Post by be4truth on 2007-07-26
> **anewguy said:**
> I think when you do that you also need to add 

Option   "SHMConfig"  "true"

to the touchpad section in xorg.conf, don't you?? (I know you do in order to use gsynaptics).:)

:KSyes, I forgot

Try this link as well 

[http://ubuntuforums.org/showthread.php?t=168581&highlight=qsynaptics]("http://ubuntuforums.org/showthread.php?t=168581&highlight=qsynaptics")

---

### Post by kbar78 on 2007-07-27
Ah yes.  I've gotten an error message while trying to use the gsynaptics package that reccomended that.  Where exactly *is* the xorg.conf file?  Moreover, is there a practical way to search for files and/or folders in Ubuntu?

Thanks again

---

### Post by anewguy on 2007-07-27
The xorg.conf file is located in the /etc/X11 directory.  You can edit it via "sudo gedit xorg.conf".

Hope it work for you - let us know how it goes!:)


Edit:  As far as searching for files, I haven't figured that out yet, but from what I saw someone recommend for something else, it might be worth trying "locate xorg.conf"

---

### Post by be4truth on 2007-07-27
I recommend that before you ever touch a config file you make a backup first. Go into the directory ( /etc/X11) and type the following into a shell:

```
cp xorg.conf xorg.conf.backup
```


The command 'locate' or 'slocate' searches a database of files on your system. This is fast! This database is by default updated once a day. You would type in the following into a shell:

```
locate xorg.conf | more
```

The '| more' part prevents that lots of lines just fly by. Go through with the 'space bar'.'Shift + Q' gets you out of it. If you have installed something new the files will not be in the file database right away but only after the next routine update. You can update the database yourself with:

```
sudo updatedb
``` 
This will take some time depending on your CPU speed and the amount of files you have on your hard drive.
Most configuration files will be in the /etc directory.

---

### Post by kbar78 on 2007-07-27
Thanks a bunch guys.  I edited the config file, rebooted and bingo - working touchpad config utility.  This seems like a simple enough fix for the program, when does the community usually release fixes for this sort of thing/update the package manager so that new users aren't dowloading broken software?  I've had to install a few things from source code(i.e. Thunderbird 2.0, Pidgin 2.0.0.2 as opposed to Gaim beta)  since Synaptics didn't include the most up to date versions of those programs.

Learning a lot about software and the open source community and having some fun along the way, thanks again!

---

### Post by anewguy on 2007-07-27
Glad we could help!  As b4truth mentioned, it is best to make a backup.  I would suggest you preface the "cp" command with "sudo " any time you are working with the xorg.conf file.  You can do the locate, and do the database update if you want to, but they aren't required to get the touchpad working.  All that is actually needed is the installation of gsynaptics and adding the line to the xoorg.conf file and restarting X (for some people who are just beginning, it may be best just to tell you to reboot).

Hope you enjoy!:)

---

### Post by Dirk Lately on 2007-07-27
I´ve installed the application (I think) and edited the conf file, but I can´t seem to find the app. I have rebooted. When I try to install it again, it says it´s already installed.

I don´t have a ¨program utility¨ menu. Where the heck is qsynaptics?

---

### Post by anewguy on 2007-07-28
I don't know about qsynaptics, but gsynaptics is run by going to system/preferences/touchpad.:)

---

### Post by Dirk Lately on 2007-07-28
Hmm. Thanks, but I ain´t got one of those!

---

### Post by anewguy on 2007-07-28
I'd try going to synaptics package manager, marking qsynaptics for removal and gsynaptics for install and applying those changes, then see what you've got.:)

---

### Post by tashmooclam on 2007-07-28
I walked over to Borders to look this up in one of the various $30+ books.
I downloaded the touchpad program: System, Administration, Synaptic Package manager. Downloaded the program.
I went to terminal: Applications, Accessories, Terminal.
I typed in "qsynaptics". 
I got a dialog showing the program, but all the buttons were faint, not active I saw a message in the dialog box.
I've no idea what the message I see means in the qsynaptics: 
"Please install the synaptics touchpad driver!" (Ihave already).
"Please enable x shared memory config in xf86 config" 
This is all as clear as mud because I don't know what or where a xf86 cofig is. 
This is becoming a serious pain, since using Firefox is extremely annoying when everything I pass the cursor over thinks I selected it.

---

### Post by kbar78 on 2007-07-28
hmmm.... I think part of this problem may be the fact that both ***g***synaptics *and* ***q***synaptics are touchpad configuration tools.

I would recommend, particularly if you're looking at this thread for help, getting rid of qsynaptics and sticking with gsynaptics.  Both packages can be obtained and removed via the package manager.  I prefer gsynaptics since it comes with a launcher and is apparantly more straightforward.


just my 2 cents

---

### Post by tashmooclam on 2007-07-28
I'll look into gsynaptics, can't hurt anything. 
Someone must tell Ubuntu that laptops come with trackpads.
Thanks.

---

### Post by ugm6hr on 2007-07-28
> **tashmooclam said:**
> Someone must tell Ubuntu that laptops come with trackpads.


Someone has. That's why it works from the start.  Just the Synaptics driver gives greater control over it, just as it does in Windows.

I would suggest you look at your xorg.conf - or post it here.  Is the problem that you want to remove the tap to click?  Or something else?

---

### Post by tashmooclam on 2007-07-28
I would have put touchpad settings under the System menu, because the default touchpad settings are almost unusable particularly when using Firefox, almost anything I pass the cursor over wants to open. It's just too darn sensitive.
Maybe others have had better luck with default. If I can't use my gmail, browse the web, the thing begins to become useless.
Here's what I see when I go to "xorg.conf" which says it's a "read only" file.

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
	Identifier	"S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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

---

### Post by anewguy on 2007-07-29
Try adding this to your xorg.conf file before the "Section Device" statement above the line about S3 graphics:


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection


Then add this after the "Inputdevice "eraser"  "SendCoreEvents" in the "Section ServerLayout":

	InputDevice	"Synaptics Touchpad"


Save the file, then be sure you have followed the previously mentioned instructions for getting rid of qsynaptics and installing gsynaptics.  Also, from personal preference, I would recommend you install network-manager-gnome (this requires network-manager as well).

When all is done log off, wait for the log on screen, hold down ctrl-alt and press the backspace key, then release all of the keys.  This will restart X using your changed xorg.conf file.  Now log on, go to system/preferences/touchpad and see how things go.:)

---

### Post by tashmooclam on 2007-07-29
Thanks, I'll give it a try maybe in a while, I've got to leave town and won't be looking at it for a couple of days.  
It looks as if I am making some real changes, hopefully it's all OK.
I did get rid of qsynaptic already, and have gsynaptic now. 
Thanks much.

---

### Post by tashmooclam on 2007-07-29
I just entered the text suggestions in the places you suggested. I was careful to make everything look identical. 
Hoever I am _not_ allowed to either "save" or "save as" in this folder.
This makes sense, as it says it is a "read-only file".

---

### Post by ugm6hr on 2007-07-29
> **tashmooclam said:**
> I just entered the text suggestions in the places you suggested. I was careful to make everything look identical. 
Hoever I am _not_ allowed to either "save" or "save as" in this folder.
This makes sense, as it says it is a "read-only file".
Before doing anything else:
```
sudo cp xorg.conf xorg.conf.backup
```

Then, to edit it, you will have to open it with:
```
sudo gedit /etc/X11/xorg.conf
```

Advice as per anewguy - although one other edit that can sometimes be necessary:
```
	Load "synaptics"
```
Put this in the Section "Module" near the start.

---

### Post by anewguy on 2007-07-29
Thanks for the addition - I've never seen it before!:)  Also, sorry if I forgot the "sudo " thing.  For all those beginners who may reading this thread, "sudo " tells Ubuntu you want to execute the following command as the "super user", a special user in LInux that has access to everything.  The /etc/X11/xorg.conf file, amongst MANY others on your system, are owned by the system and by default users do not have write access to it.  In order it edit it, you do indeed need to type:

[COLOR="Red"]sudo gedit xorg.conf[/COLOR]

Most of the time, the how-to or instructions you will be receiving will tell you or show you when you need to use "sudo ".  When you try something and it says you don't have permissions to do it, try prefacing it with "sudo " - if it works then you know you need to investigate the permissions you have via system/administration/users and groups. 

:)

---

