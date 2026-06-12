---
title: "Desktop Effects: the composite extension is not available"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by morweni on 2007-09-27
*shakes her fist*

Just a quick intro so you realise what kind of noob you're dealing with ;). I've bounced from distro to distro and end up back on xp for gaming purposes. I've done a lot of research on Ubuntu and decided tonight to toast all partitions despite the boyfriends objection to making the switch. Now I have this problem :\

I installed **7.04** tonight and wanted to straight away start customizing and begin learning. I've only played with the GUI of linux and scratched the shell commands (get, ls bla bla) but defintealy willing to learn >.>

[I]Tried installing the ati x 1400 mobility drivers (installer off their site(and immediately receive:

Could not open the file /home/adria/Desktop/ati-&#8230;ler-8.40.4-x86.x86_64.run.

Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again.[/I]

I have been reading a few threads and am unable to find a fix for 
[B]
"composite extension is not available "

Have an Acer Aspire 5670 WLMI, x1400 mobility ati card..[/B]

any help would be appreciated!!!

P.S. sorry to add to the existing threads about this issue. But either the fixes seem too advanced for what I know currently or their for nvidia cards or they haven't worked for me yet >.>

---

### Post by jordanmthomas on 2007-09-27
Ok, to install the driver you need to open up a terminal (applications -- accessories -- terminal)
from here, you need to go onto your desktop
```
cd ~/Desktop
```
Now, the reason the text editor is opening the file is that it is a normal file until you tell it it can be executed, so let's make it executable.
```
sudo chmod +x ati-&#8230;ler-8.40.4-x86.x86_64.run
```
**when you get to the ati part, start typing ati and then hit tab, and the rest of the name will be filled out**

You will be asked for your password (you won't see it when you're typing, but it is being taken).

Now, the file is executable and all that's left is to execute it:
```
sudo ./atiwhateverthefilenameiscalled
```
again, use tab to fill out the filename.

To fix the composite error, do this from your terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
This will open your text editor and a pretty confusing-looking file.
Just add this to the end.
```
Section "Extensions"
        Option      "Composite" "enable"
EndSection
```
Save it and close it.
Now, log out and then back in and see if that helps any.

---

### Post by angryfirelord on 2007-09-27
I would use this guide, as it's more up-to-date & shows you how to generate deb packages for the ATI drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually")

---

### Post by jordanmthomas on 2007-09-27
> **angryfirelord said:**
> I would use this guide, as it's more up-to-date & shows you how to generate deb packages for the ATI drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually")

+1  I'd suggest it too.

By the way, does the driver not offer to install itself in the Restricted Driver manager?  I don't know, since I don't use Ubuntu, but I thought that was something new they had out for it.

---

### Post by Adramelech on 2007-09-28
yes, you should use restricted manager, installing drivers by hand can be hard and can let you on a shell screen whiout GUI, thats not good if you are just starting.

---

### Post by jordanmthomas on 2007-09-28
I'd also like to say that it's MUCH easier to get dekstop effects to work on an ati card using the open-source driver instead of ati's.

All that's necessary is adding the composite section to your xorg.conf as I've outlined above.

---

### Post by erfahren on 2007-09-28
First, you shouldn't have to install the driver off of the ATI site. There is a ATI proprietary driver (albiet an older version) included with (and configured for) Feisty. It just isn't enabled by default.

To enable it go to System > Adminsration > Restricted Drivers Manager check it and reboot.

Secondly, for reasons being, the driver doesn't support desktop effects on it's own (even the newer version at this time). You need to set up a XGL session in order to run desktop effects. [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

To create a XGL session to run desktop effects (Compiz-Fusion, etc.) there's this guide: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

Note: ATI's support for desktop effects is poor. Some cards are worse that others. I've noticed some having problems with the x1400 card. That guide works for my x1100 card though.

EDIT: a few people answered while i was typing mine! The open-source driver worked well for desktop effects for me too, but I had problems with my power management settings with it.

---

### Post by morweni on 2007-09-28
Thank you very much! I've played around with an account on a friend's suse machine, learned how to move around in there but that was a long time ago so this is baby steps in remember how to move around in the shell rofl ^_^.


Thank You, you're wonderful ^^

Now it's providing a:  ** 'Desktop effects could not be enabled'** .  rofl >.>

---

### Post by morweni on 2007-09-28
sorry forgot to include:

Tried  to set up a XGL session in order to run desktop effects. [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

method 1 was attempted.. just rebooting now :)

---

### Post by morweni on 2007-09-28
Ok, rebooted into XGL using the 1st method of intstallation. Started the session with XGL and the display was completely distorted.. Tried it again to be sure before going back to regular gnome.. no dice :(


**Desktop effects could not be enabled**
Any ideas? :)

Thank you!

---

### Post by morweni on 2007-09-28
Also just tried :  How To : Compiz Fusion for ATI cards + Xgl in Feisty
**[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)**

After getting to this point:
[I] 
Code:

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

Now make this script executable by pasting this into a terminal:

Code:

sudo chmod a+x /usr/share/xsessions/xgl.desktop

**Now test your login. Logout, click sessions and chose GNOME with XGL. If you get to the desktop you're now very close.[/I]**


[COLOR="DeepSkyBlue"]Again, desktop was all distorted :confused:[/COLOR]

---

### Post by erfahren on 2007-09-28
boot into your regular Gnome session (use the one that says "Run Xclient script") and run this in the terminal:
```

fglrxinfo

```
the output should look something like this:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

if it says anything about Mesa go to System > Administration > Synaptic Package Manager (click the Reload button to update everything) and then do a search for "fglrx". Re-install the following packages: 
xorg-driver-fglrx and linux-restricted-modules

reboot back into the Xclent script session and run "fglrxinfo" again

...and make sure you have the following in your /etc/X11/xorg.conf file:

at the very end of it you should have:
```

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```
(I know someone earlier recommended an entry that had "Composite" enabled, but that isn't correct. The fglrx driver doesn't support that on its own which is why we need to run a XGL session (the way I understand it anyway).

Also make sure that under the - Section "Module" - near the top it has this in there (it should): Load  "dri"

(If your curious my full /etc/X11/xorg.conf file is posted [here](http://ubuntuforums.org/showpost.php?p=3253280&postcount=11) )

Restart X by pressing Crtl+Alt+Backspace and change sessions into the GNOME with XGL and see if that helped.

---

### Post by jordanmthomas on 2007-09-28
> **erfahren said:**
> 
(I know someone earlier recommended an entry that had "Composite" enabled, but that isn't correct. The fglrx driver doesn't support that on its own which is why we need to run a XGL session (the way I understand it anyway).


Sorry about that, I wasn't sure if they were going to keep the ati (open) drivers or go with fglrx.
You are correct though.

---

### Post by LuisC-SM on 2007-09-28
> **jordanmthomas said:**
> Ok, to install the driver you need to open up a terminal (applications -- accessories -- terminal)
from here, you need to go onto your desktop
```
cd ~/Desktop
```
Now, the reason the text editor is opening the file is that it is a normal file until you tell it it can be executed, so let's make it executable.
```
sudo chmod +x ati-&#8230;ler-8.40.4-x86.x86_64.run
```
**when you get to the ati part, start typing ati and then hit tab, and the rest of the name will be filled out**

You will be asked for your password (you won't see it when you're typing, but it is being taken).

Now, the file is executable and all that's left is to execute it:
```
sudo ./atiwhateverthefilenameiscalled
```
again, use tab to fill out the filename.

To fix the composite error, do this from your terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
This will open your text editor and a pretty confusing-looking file.
Just add this to the end.
```
Section "Extensions"
        Option      "Composite" "enable"
EndSection
```
Save it and close it.
Now, log out and then back in and see if that helps any.

Congrats...
What a nice and clean way to explan it...
Regards
Luis

---

### Post by morweni on 2007-09-28
Thank you for the absolutely wonderful explanations :) but still to no avail (when starting with the gnome + xgl session display is all distorted.. :(

Alrighty, I went in and updated everything related to xorg-driver-fglrx and linux-restricted-modules in that synaptic package manager... 


checked fglrxinfo: before and after the reboot.. still is
```

adria@Adria:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

This is my xorg.conf
```

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
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

off to work but will try w/e is suggested the second i'm at home =) ty ^^

---

### Post by morweni on 2007-09-29
bumping for aide :redface:

---

### Post by LuisC-SM on 2007-09-29
> **morweni said:**
> Thank you for the absolutely wonderful explanations :) but still to no avail (when starting with the gnome + xgl session display is all distorted.. :(

Alrighty, I went in and updated everything related to xorg-driver-fglrx and linux-restricted-modules in that synaptic package manager... 


checked fglrxinfo: before and after the reboot.. still is
```

adria@Adria:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

This is my xorg.conf
```

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
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Generic Video Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

off to work but will try w/e is suggested the second i'm at home =) ty ^^
Which video card do u have? ... Intel?

---

### Post by Ant_Merlin on 2007-09-29
Hi, this is ATI driver issue still as its showing Mesa rather than Opengl. There 2 ways I have found to be best at installing ATI drivers. First is:

> 
Type this into a terminal:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --force --initial
sudo aticonfig --overlay-type=xv

The second way is to install envy, I call it cheating cause you dont get to use the terminal (something as a noob myself I try and do to fix anything) but it is very easy.

Make sure you remove driver first, before installing new one (there is an option in envy to remove a driver first)

[http://albertomilone.com/ubuntu/nvid...untu11_all.deb]("http://albertomilone.com/ubuntu/nvid...untu11_all.deb")

Let me know how u get on, I have an ATI x1650 and it runs fine now.

---

### Post by morweni on 2007-09-30
```


adria@Adria:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```

As per ** Ant_Merlin**'s question I am running an ATI x1400 mobile gfx card on a Acer Aspire 5670 lappy. 

At this point it isnt souly a matter of getting Desktop Effects to work, but rather... the darn thing working overall lol. 


btw - [http://albertomilone.com/ubuntu/nvid...untu11_all.deb](http://albertomilone.com/ubuntu/nvid...untu11_all.deb) giving me an error as the entire url is not suppled :) 


:confused: /cry, is there any hope for me? :P

---

### Post by morweni on 2007-09-30
Installed envy, went over all the responses on the thread to be sure I wasn't a dolt and still no dice.

EDIT: now after installing envy i get the composite device error, i'll have to go back and start the process again... in the mean time any thoughts?
:confused:

---

### Post by Ant_Merlin on 2007-10-01
Hello, Sorry about the URL paste must have missed a bit off, you say you are getting composite error, is this in an XGL session or a normal Gnome Session? If its in XGL you will get that error but it doesnt mean your card isnt  installed ok. Try DISPLAY=:0 in front of fglrxinfo if you are in XGL.
If not your driver def not installed ok.

---

