---
title: "Desktop effects could not be enabled - Nvidia TnT2"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by mechchild on 2007-12-01
Hello all

I have searched high and low and cannot find a solution. I for whatever reason cannot enable desktop effects. This is the error I get "Desktop effects could not be enabled"

I am out of Ideas. Any help would be great. I love to learn. So please Help. PLease tell me what you would like to see and I will post it. I am Running a Nvidia Riva TnT2. I have enabled the restricted drivers. What now??

Thanks 
Tim

---

### Post by schauerlich on 2007-12-01
You might not be running X from the drivers. Have you tried logging in/out since enabling them?

---

### Post by mechchild on 2007-12-01
Yes i have tried logging out and back in. Still no change

---

### Post by schauerlich on 2007-12-01
It's possible you may need to reconfigure xorg.conf. To do this, first run:

```
cd /etc/X11
```
To change into that directory.
```
sudo cp xorg.conf xorg.conf.backup
```
To make a copy of your current configuration. Now it's time to reconfigure.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Will bring you to the xorg configuration screen. From there, select the nv driver and whatever resolution you need. If it asks you anything else, the defaults are usually fine. Once you've done that, report back.

---

### Post by mechchild on 2007-12-01
after i put all that in. this is what i get

> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071201131744


any idea? no where I can select resolution or driver ect.

---

### Post by fenian on 2007-12-01
What do you get if you run....

> glxinfo | grep direct

---

### Post by schauerlich on 2007-12-01
Does that come up after
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
?
It should take you to a text based reconfigure program. Try hitting Ctrl+Alt+f1 to change into a full screen terminal, log in, and run the last command again. To get back to the GUI, hit Ctrl+Alt+f7

---

### Post by mechchild on 2007-12-01
if I do glxinfo | grep i get:

> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


---

### Post by mechchild on 2007-12-01
i get the same thing in full screen terminal ??

---

### Post by schauerlich on 2007-12-01
Well, all it's telling you is that you might be overwriting your customized settings, which is no big deal because we already backed them up. Did you hit enter after it came up? Or, y and then enter?

---

### Post by mechchild on 2007-12-01
yes,i hit y, and or enter still no difference

> tim@tim-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for tim:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071201133743
tim@tim-desktop:~$ y
bash: y: command not found
tim@tim-desktop:~$ 
tim@tim-desktop:~$ 
tim@tim-desktop:~$ 



---

### Post by irish_flu on 2007-12-01
IIRC that video card either as 16 or 32 MB of RAM on it.  This is just speculation, but maybe desktop effects just say "oh, heck no" and shut off?

---

### Post by fenian on 2007-12-01
GLX isn't enabled,you need to enable it .Please post your xorg.conf file.

---

### Post by mechchild on 2007-12-01
ok here you go:

> # xorg.conf (xorg X Window System server configuration file)
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
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1916W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Acer AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

---

### Post by fenian on 2007-12-01
Try this run...
> 
sudo nvidia-glx-config enable

then

> sudo gedit /////etc/X11/xorg.conf

to the Section "Screen" add the line...

Option "AllowGLXWithComposite" "1"

save exit and restart X (ctrl+alt+backspace).

Try to enable effects.On a side note even if you do manage to get the effects working the card may simply not be powerful enough to provide good results,it will probably slow your system down considerably.

---

### Post by mechchild on 2007-12-01
I understand that. I just want to get it to work. If it slows down my system, then fine, I will change video cards, But untill I try I wont know..

I have tried the above but still get the Desktop effects could not be enabled. 
Im frustrated on one note, but also, I just wanna see if I can do it i guess.\

I do appreciate all the help.

Anything else I can try?

---

### Post by fenian on 2007-12-01
I would suggest using the envy script to make sure you have the most up to date nvidia drivers.You can find it [here]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by mechchild on 2007-12-01
I try to download and install it and this is what I get.

Error: Dependancy is not satisfieable: xserver-xorg-dev


WTF is that? 

Nothing but problems

---

### Post by erm27 on 2007-12-01
sudo apt-get install xserver-xorg-dev 

It's missing the development files for xorg?

---

### Post by overdrank on 2007-12-01
Hi and I understand you are trying to get the desktop effects but I had a similar video card in  a laptop and it is a no go. But if you insist on trying to continue, I wish you the best of luck! :)

---

### Post by mechchild on 2007-12-01
I try to install envy. I wont happen. says dependency is not available for ect. ect. ect .. So i go and search and find the file - download - and then again it says dependency not satisfiable: 

untill i get to libxau6 , which is installed already. I dont understand why Im stuck here. WHy cant it ssee that its installed already?

---

### Post by overdrank on 2007-12-01
> **mechchild said:**
> I try to install envy. I wont happen. says dependency is not available for ect. ect. ect .. So i go and search and find the file - download - and then again it says dependency not satisfiable: 

untill i get to libxau6 , which is installed already. I dont understand why Im stuck here. WHy cant it ssee that its installed already?

Hi have a look here
[http://ubuntuforums.org/search.php?searchid=32306872](http://ubuntuforums.org/search.php?searchid=32306872)
:)

---

### Post by mechchild on 2007-12-01
Already  have that.. still no help

---

