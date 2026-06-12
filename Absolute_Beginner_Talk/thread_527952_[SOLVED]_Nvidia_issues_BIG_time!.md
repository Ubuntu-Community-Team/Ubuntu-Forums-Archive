---
title: "[SOLVED] Nvidia issues BIG time!"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by kerrymorgan1 on 2007-08-17
I have done another mistake:confused: again sorry

and now it has completely locked me out.... i try to start it in every other option (recovery mode) but I know what i did i was following another thread on how to install the drivers and this happened can someone please help me uninstall what ive done just so i can see the desk top again..........
right now i am in a black and white screen i have logged in and waiting further instruction.....
please help

when i type in "sudo /etc/init.d/gdm stop" or start a blue screen comes up and it says Failed to start the X server it wasn't set up

it diagnoses the issue and it says under Nvidia No matching device detected

8600gt nvidia

---

### Post by Synflux on 2007-08-17
Hi,

Have you tried:

sudo dpkg-reconfigure xserver-xorg

?

---

### Post by Dark Star on 2007-08-17
Are ur drivers up to date  :) If not try updating it via Envy Script :)

---

### Post by kerrymorgan1 on 2007-08-17
just did it says x server-org is not installed

whats the code to install it? sorry mate im really new

---

### Post by kerrymorgan1 on 2007-08-17
> **Dark Star said:**
> Are ur drivers up to date  :) If not try updating it via Envy Script :)

i just installed Envy i went into Nvidia and it popped up with something, i went into applications>add/remove serched for Nvidia and installed the second thing there it said i had to restart i did that and now i can't get back in to change anything i have to do it from the black and white dos screen

---

### Post by kerrymorgan1 on 2007-08-17
from the black and white screen can anyone help me undo what ive done?

---

### Post by phenest on 2007-08-17
When you say "black and white screen", do you mean a black screen with white text. I'm guessing so. Login normally (username and password). Type:
```
sudo dpkg-reconfigure xserver-xorg
```
and re-type your password. The screen will turn blue and it will ask some questions. You can just keep pressing Enter for most of it (use Tab to highlight the OK on some questions. Just keep a look out for a list of driver names (near the beginning). It may have "nv" already highlighted. Provided you have installed the correct driver, you should see nvidia in the list. Use the cursor keys to highlight it and the Enter through the remainder of the screens until you return to a white on black prompt again. Type:
```
sudo reboot
```
and let us know the outcome.

---

### Post by Hobo Joe on 2007-08-17
> **kerrymorgan1 said:**
> from the black and white screen can anyone help me undo what ive done?

Yes, since you already have Envy, you can just run it in text mode:
```

envy -t

```
After than press UNinstall nVidia drivers, then once it's done, install nvidia drivers. Make sure to let it reconfigure your xorg for you.

---

### Post by kerrymorgan1 on 2007-08-17
> **phenest said:**
> When you say "black and white screen", do you mean a black screen with white text. I'm guessing so. Login normally (username and password). Type:
```
sudo dpkg-reconfigure xserver-xorg
```
and re-type your password. The screen will turn blue and it will ask some questions. You can just keep pressing Enter for most of it (use Tab to highlight the OK on some questions. Just keep a look out for a list of driver names (near the beginning). It may have "nv" already highlighted. Provided you have installed the correct driver, you should see nvidia in the list. Use the cursor keys to highlight it and the Enter through the remainder of the screens until you return to a white on black prompt again. Type:
```
sudo reboot
```
and let us know the outcome.

that worked a charm ........ but now other things have crapped out..... i'll give it a restart then see what happens

when it says restart X does that mean the whole computer?

---

### Post by Hobo Joe on 2007-08-17
> **kerrymorgan1 said:**
> that worked a charm ........ but now other things have crapped out..... i'll give it a restart then see what happens

when it says restart X does that mean the whole computer?

No, you can restart X by pressing (ALT + CTRL + Backspace).

Also, if you still have problems, try what I suggested, this may be a driver issue.

---

### Post by Frak on 2007-08-17
just means press
Ctrl+Alt+Backspace

---

### Post by kerrymorgan1 on 2007-08-17
you guys are amazing! all of that did wonders reset everything and it's fine now

I am where i was 1.3 hours ago.....

I go applications>system>nvidia settings it says im not using "Nvidia X driver" how do i change that? is there more codes?

---

### Post by Hobo Joe on 2007-08-17
Paste the output of:
```

glxinfo

```
And also paste your xorg file:
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by phenest on 2007-08-17
It would also be helpful if you told us which nvidia driver you installed.

---

### Post by kerrymorgan1 on 2007-08-17
it is still saying "nv" and generic video card

do i have to start all over again?

---

### Post by kerrymorgan1 on 2007-08-17
> **Hobo Joe said:**
> Paste the output of:
```

glxinfo

```
And also paste your xorg file:
```

sudo gedit /etc/X11/xorg.conf

```

kerryandjane@kandj-desktop:~$ glxinfo
Segmentation fault (core dumped)

is all i have got

---

### Post by kerrymorgan1 on 2007-08-17
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
	Identifier	"Generic Video Card"
	Driver		"nv"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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

sorry mate

---

### Post by phenest on 2007-08-17
You need to install:
```
sudo apt-get install nvidia-glx
```
After installing, restart the computer and then try nvidia-settings again.

---

### Post by Hobo Joe on 2007-08-17
> **kerrymorgan1 said:**
> kerryandjane@kandj-desktop:~$ glxinfo
Segmentation fault (core dumped)

is all i have got

> **kerrymorgan1 said:**
> 

Section "Device"
	Identifier	"[COLOR="Red"]Generic Video Card[/COLOR]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
EndSection


That's the problem there.

Also there is a SERIOUS issue if you are unable to run the command 'glxinfo'. Reboot and try again.

---

### Post by Frak on 2007-08-17
Bad voodoo if glxinfo doesn't work and APT doesn't catch it :(

---

### Post by kerrymorgan1 on 2007-08-17
> **phenest said:**
> When you say "black and white screen", do you mean a black screen with white text. I'm guessing so. Login normally (username and password). Type:
```
sudo dpkg-reconfigure xserver-xorg
```
and re-type your password. The screen will turn blue and it will ask some questions. You can just keep pressing Enter for most of it (use Tab to highlight the OK on some questions. Just keep a look out for a list of driver names (near the beginning). It may have "nv" already highlighted. Provided you have installed the correct driver, you should see nvidia in the list. Use the cursor keys to highlight it and the Enter through the remainder of the screens until you return to a white on black prompt again. Type:
```
sudo reboot
```
and let us know the outcome.

i did this i didn't know what to type so i just kept pressing enter........ i can go do it again and change things for sure but i just don't know what to change it to.

thanks for your help i'll restart

---

### Post by kerrymorgan1 on 2007-08-17
hey don't worry about it it does seem very serious i'll just reinstall the sucker again 
thanks

---

### Post by Hobo Joe on 2007-08-17
Yeah, I'm not sure what segmentation fault is, but there is nothing that should stop you from running glxinfo, especially without telling why.

---

### Post by Frak on 2007-08-17
Segmentation Fault is when a process wants to overwrite the OS protected section of the RAM. (Or Swap)

---

### Post by Hobo Joe on 2007-08-17
> **Frak said:**
> Segmentation Fault is when a process wants to overwrite the OS protected section of the RAM. (Or Swap)

D:

Yeah, a re-install would be a good idea.

When you reinstall do envy first. :)

---

### Post by steve.horsley on 2007-08-17
Before reinstalling, try this command:
**sudo aptitude install nvidia-glx-new**
then restart X with Ctrl-Alt-Backspace

---

