---
title: "&quot;Failed to start the x server&quot; - Sorry, new user, same problem"
date: 2007-07-23
forum: Apple PPC Users
---

### Post by madog on 2007-07-23
EDIT: The first thing I see on my screen after hitting enter at the boot screen, I get the first ominous error for my firewire:

```
[    51.093868] ieee1394: Error parsing configrom for node 0-00:1023
```

Anyway, after having a similar problem with Yellow Dog Linux [before realizing there was a PPC version of Ubuntu] even though it did successfully install, I figured I would give Ubuntu a try after hearing so many good things about it.

Well, seems I'm having the same problem as everybody else, the x server will not load. When checking out the xorg file, it looks as though it is autodetecting all of my hardware perfectly. It knows exactly what monitor I have,  Dell D1626HT [on second thought it might not be exact but it does know it's a Dell; will check soon], along with the exact GPU, Radeon 8500, installed. However, whenever I try to reconfigure it, modify it or anything else, I just get different errors all causing the x server to fail. From other posts I have tried the settings:

```
sudo nano /etc/X11/xorg.conf

In the "Monitor" section add the following lines:

Code:

HorizSync                36-52
VertRefresh              36-60

It should look like this:
Code:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	36-52
	Vertrefresh	36-60
EndSection

Now go to the "Screen" section. Remove all other resolution than "640x480". So it will look like this:

Code:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"640x480"
	EndSubSection
EndSection

Click F2 to save and quit. Now write:
Code:

sudo killall gdm
sudo gdm


``` 

and another:

```
Section "ServerLayout"
Identifier "single head configuration"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "Monitor"

### Comment all HorizSync and VertSync values to use DDC:
Identifier "Monitor0"
ModelName "Samsung SyncMaster 150N/152N/153N"
### Comment all HorizSync and VertSync values to use DDC:
HorizSync 30.0 - 61.0
VertRefresh 56.0 - 75.0
Option "dpms"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "radeon"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```

None of these configs have worked, like I stated before they all cause different errors all resulting in the x server failing. When trying to manually reconfigure with all sorts of options I don't understand the same occurs.

What usually happens is that when I make any settings to the xorg file, kill the gdm and attempt to restart it the screen the screen will flicker 3 times each saying something to the effect of, "The x server is now disabled, restart gdm when it is reconfigured correctly" and then after the third time I get the "Failed to start" message.

So far it seems that my 5th lifetime attempt at installing a variation of linux on my machine has failed [4 at YDL on 3 different machines, this being my first at Ubuntu]. I would actually like to put forth some effort into this attempt if anyone can help me, otherwise it seems I'll have to wait another few years to test it out.

Sorry about the images but I don't have the time or application needed to merge them at the moment.

[IMG]http://i110.photobucket.com/albums/n107/munderdown/IMG_0024.jpg[/IMG]

and to continue the image:

[IMG]http://i110.photobucket.com/albums/n107/munderdown/IMG_0025.jpg[/IMG]

Any sort of help would be appreciated, however, it seems this error is unique to each system and not all fixes posted are applicable. Thank you.

---

### Post by mckryptyk on 2007-07-23
Well here is what mine looks like, hope that helps.

Have you checked the file permissions on /etc/X11/xorg.conf ?

Have you looked up your monitors resolutions from the manufacturer's website ?

Cheers

Edit

---

### Post by stmiller on 2007-07-23
Have you tried:

```
sudo dpkg-reconfigure xserver-xorg
```

---

