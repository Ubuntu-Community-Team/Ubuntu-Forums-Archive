---
title: "Extrange messages running Firefox"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-08-29
Hi ! I've just installed the Firefox package and when I run the command "firefox" or "mozilla" appears the following message:
```

fredscripts@laptop:~$ firefox
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device 
```

and then the Firefox get opened and run perfectly, but that message don't feel good. Can anyone tell me what that message mean and if I can avoid it says it to me every time I run firefox? 

Thanks!!!

---

### Post by oilchangeguy on 2007-08-29
what firefox package did you install? because the browser already comes pre-loaded in ubuntu.

---

### Post by fredscripts on 2007-08-29
I run (Kubuntu 7.04):

```
sudo apt-get install firefox 
```

and then

```
sudo apt-get update
```

---

### Post by nikef on 2007-08-29
[QUOTE=fredscripts;3275163]I run (Kubuntu 7.04):

```
sudo apt-get install firefox 
```






you dont need 2 it comes pre-loaded :)

---

### Post by FuturePilot on 2007-08-29
> **nikef said:**
> 
you dont need 2 it comes pre-loaded :)
Kubuntu doesn't come with Firefox. Those errors are caused by a section in your xorg.conf file. They're harmless, but annoying. If you want to get rid of them.
```
kdesu kate /etc/X11/xorg.conf
```
Find these sections and comment them out by putting a # in front of each line. It should look like this
```
#Section "InputDevice"
	#Driver		"wacom"
	#Identifier	"stylus"
	#Option		"Device"	"/dev/input/wacom"
	#Option		"Type"	"stylus"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
	#Driver		"wacom"
	#Identifier	"eraser"
	#Option		"Device"	"/dev/input/wacom"
	#Option		"Type"	"eraser"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
	#Driver		"wacom"
	#Identifier	"cursor"
	#Option		"Device"	"/dev/input/wacom"
	#Option		"Type"	"cursor"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

```
Then comment out these 3 lines further down
```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	[COLOR="Red"]#Inputdevice	"stylus"	"SendCoreEvents"
	#Inputdevice	"cursor"	"SendCoreEvents"
	#Inputdevice	"eraser"	"SendCoreEvents"[/COLOR]
EndSection
```
Save.
Log out and restart X Ctrl+Alt+Backspace

---

### Post by schorsch on 2007-08-29
@FuturePilot: Thanks for resolving this problem that was annoying me, too.

---

### Post by fredscripts on 2007-08-29
Oh!!! Perfect explained! Thank you very much it worked!

Just for curiosity, that message appears on any Kubuntu 7.04 system? or I did something that cause their appearance?

---

### Post by DM was on fire! on 2007-08-29
I've never had that running Firefox, but I've had it running Konqueror.
Makes me wonder if it's maybe a KDE glitch? o_o

---

### Post by schorsch on 2007-08-29
.... more an xorg glitch as I had this error when starting VirtualBox in a terminal running under Ubtunu 7.04 and Gnome .....

---

### Post by fredscripts on 2007-08-29
By the way (don't think it's necessary to open another thread) how I set Firefox as the default web browser? Thanks in advise!

---

### Post by schorsch on 2007-08-29
Using Gnome you can tune this parameter with "gconf-editor" but as you are running KDE .... sorry, I have no idea :-(

---

### Post by fredscripts on 2007-08-29
> **schorsch said:**
> Using Gnome you can tune this parameter with "gconf-editor" but as you are running KDE .... sorry, I have no idea :-(

What a pity! Let's see if someone using KDE know it!:)

---

