---
title: "mighty mouse on hardy heron"
date: 2008-05-06
forum: Apple Hardware Users
---

### Post by dasistwas on 2008-05-06
Hi,

I have a apple mighty mouse used with ubuntu. the basics work fine, but how do I get the functions the mighty mouse provides on os x like:

[LIST]
[*]horizontal scroll
[*]use the side buttons for advanced compiz features
[*]right mouse click with ctrl
[*]click on the scroll button + left mouse click to trigger compiz action
[*]and so on
[/LIST]

I already read the mighty mouse postings for the other versions of ubuntu (gutsy, etc.), but the solutions provided there don't work on hardy.

Any help is greatly appreciated.

Best regards,
david

---

### Post by gforster on 2008-05-06
David isn't the only one with this problem!  the guides for Gutsy and older just don't work as many things seem to have changed in Hardy. Normal functions work for me just as above, but no horizontal scroll or squeeze (button 8), at least not the way it 'should.' Right now it is acting as copy/paste.  not sure how or why.  

horizontal scrolling is the biggest "missing feature."

---

### Post by cyberdork33 on 2008-05-06
the horizontal scrolling and extra buttons are the same on the mighty mouse as for any other pc mouse. so, even "non-mac" how-tos should be able to address this.

Getting certain buttons to trigger compiz actions is completely dependent on compiz settings... ```
 sudo apt-get install compizconfig-settings-manager
```

you can do the key+click trick as in the Macbook wiki:
[https://help.ubuntu.com/community/MacBook#head-b0c1214684daee45c97d31d9113d7719accdf060](https://help.ubuntu.com/community/MacBook#head-b0c1214684daee45c97d31d9113d7719accdf060)

---

### Post by blurg on 2008-05-06
Your mighty mouse should right click when you click the right hand side of it? - even though it looks like it has one big button not two, and OS X is set up by default to play with that silly conceit, it does have two functioning mouse buttons. My right mouse click works in both OS X (once I set it up in prefs) and in Ubuntu (no prefs required).

As for squeezy sides, scroll click, and horizontal scrolling in Ubuntu - I haven't gotten around to playing with those yet so I look forward to answers to your questions :)

---

### Post by dasistwas on 2008-05-07
Thank you, that was an excellent hint... I am working now 4 months with this mouse and never discovered this feature (the right mouse click, even mighty mouse seems not to have one)...

I am feeling silly now, but I am happy :-)

Thanks a lot

---

### Post by gforster on 2008-05-08
I now have horizontal scrolling and buggy squeeze buttons working under Hardy using btnx. For horizontal scrolling I set the right and left as Key_right and Key_left. I set the squeeze buttons to trigger a compiz action and they work sometimes.

---

### Post by goaran on 2008-05-09
@ gforster

could you pleas tell how you got it working ?? 
i had it working under gusty but on hardy i dont know how to.

thanks in advance

---

### Post by goaran on 2008-05-09
OK .. found out how to get it working without btnx:

first find your mouselocation:
```
find /dev/input/by-id/ -name "*event-mouse"
```

then add to the xorg.conf 

```
Section "InputDevice"
        Identifier  "mightymouse"
        Driver      "evdev"
        Option      "Device" "/dev/input/by-id/usb-Mitsumi_Electric_Apple_Optical_USB_Mouse-event-mouse"
        Option      "RelHWHEELOptions"      "invert"
EndSection
```

and to the serversection (at the bottom of xorg.conf 
```
   InputDevice     "mightymouse" "SendCoreEvents"
```

thats it...

---

### Post by todivefor on 2008-05-15
Goaran,

I am very new to Ubuntu, so bear with me.  I can't get this to work.  The find /dev/input/by-id/ -name "*event-mouse" command I assume is to get information to put into the option "device" entry that follows???  When I issue the find comand, I get, " No such file or directory."

You also say add entry.  I take this to mean to add it after the existing entry?

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ps/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
        Identifier  	"mightymouse"
        Driver      	"evdev"
        Option      	"Device" "/dev/input/by-id/usb-Mitsumi_Electric_Apple_Optical_USB_Mouse-event-mouse"
        Option      	"RelHWHEELOptions"      "invert"
EndSection

This does not work for me. Is that because my option  "device" is not correct?

---

### Post by todivefor on 2008-05-15
I commented out the first Input section" and now it works fine.

---

### Post by gforster on 2008-05-15
OK, I made an idiotic mistake in while messing around with other files and decided to wipe and do a fresh install (it has been upgrade after upgrade since Breezy on my system).

Anyway, when i did the fresh install and paired up my bluetooth mighty mouse, everything worked except horizontal scrolling. Even the squeeze buttons work just fine. I personally have them mapped to the compiz-fusion action "scale" which is equivalent of mac's "expose" feature.

Through btnx I can map buttons 4 & 5 (the horizontal scroll) to be a key combo. If i do Key_right and Key_left, I can, in some apps, scroll right and left. Unfortunately, this does not truly emulate horizontal scrolling. 

I will try with xorg.conf, but I don't want to disable my touchpad (it is a laptop).

---

### Post by jamescoy on 2008-05-16
> **goaran said:**
> OK .. found out how to get it working without btnx:

first find your mouselocation:
```
find /dev/input/by-id/ -name "*event-mouse"
```

then add to the xorg.conf 

```
Section "InputDevice"
        Identifier  "mightymouse"
        Driver      "evdev"
        Option      "Device" "/dev/input/by-id/usb-Mitsumi_Electric_Apple_Optical_USB_Mouse-event-mouse"
        Option      "RelHWHEELOptions"      "invert"
EndSection
```

and to the serversection (at the bottom of xorg.conf 
```
   InputDevice     "mightymouse" "SendCoreEvents"
```

thats it...

I'm using Parallels and can't find this driver. Is the Mighty Mouse driver installed by default elsewhere? Thanks.

---

### Post by cyberdork33 on 2008-05-16
> **jamescoy said:**
> I'm using Parallels and can't find this driver. Is the Mighty Mouse driver installed by default elsewhere? Thanks.it is just a normal mouse driver, nothing specifically mightymouse about it.

Running in Parallels is not quite the same though. your mouse is likely emulated though a virtual interface in Ubuntu. In reality, you are not connecting the mouse to the VM, you are connecting it to the host OS the inputs of which are "translated" into the VM. I don't quite know how parallels handles this though. You might have to get help on this subject in the virtualization forum or maybe in the parallels boards.

---

### Post by jamescoy on 2008-05-20
> **goaran said:**
> OK .. found out how to get it working without btnx:

first find your mouselocation:
```
find /dev/input/by-id/ -name "*event-mouse"
```

then add to the xorg.conf 

```
Section "InputDevice"
        Identifier  "mightymouse"
        Driver      "evdev"
        Option      "Device" "/dev/input/by-id/usb-Mitsumi_Electric_Apple_Optical_USB_Mouse-event-mouse"
        Option      "RelHWHEELOptions"      "invert"
EndSection
```

and to the serversection (at the bottom of xorg.conf 
```
   InputDevice     "mightymouse" "SendCoreEvents"
```

thats it...

I'm trying to get my Mighty Mouse options going and am using Parallels. I think your post here refers to a "regular" install of Ubuntu, but might you have any idea of where I could look to find the Mighty Mouse driver? On my system, there is no directory dev/input/by-id.  Do I have other options?

---

### Post by rossguy on 2008-07-08
Hey Everyone, 

I am EXTREMELY new to UBUNTU and still figuring out how everything works. I am trying to connect my blue tooth mighty mouse and having troubles. I have installed every blue tooth file Hardy had to offer. It asked me for a pass key and it is paired and trusted but still will not do anything. When I go to blue tooth preferences the mouse is listed as a bonded device and it looks like it keeps connecting and disconnecting. If anyone can help me in easy to understand for a new user language I would really appreciate it. Thanks in advance for any help.

---

### Post by Zaff on 2009-05-05
Hi guys,
I wanted to use the horizontal scroll on my mighty mouse so I enabled the evdev driver as indicated in this topic. It works however text selection using the mouse doesn't work the same as it used to. Instead of selecting all text from one point to another while left mouse button is pressed, it will select until I reach the end of a word and then start selecting the next. 
Is there an option that could tell evdev to behave like the regular mouse driver on that particular point ? I haven't noticed anything else, but since this is very annoying I'm going back to the previous driver (I don't need horizontal scroll that badly.

Thanks for the help.

---

### Post by cyberdork33 on 2009-05-05
> **Zaff said:**
> Instead of selecting all text from one point to another while left mouse button is pressed, it will select until I reach the end of a word and then start selecting the next. 
I really don't know why your mouse driver would make a difference in this aspect. Are you sure that the driver change is the only thing that could be causing this functionality change?

---

### Post by Zaff on 2009-05-06
Well here's my xorg.conf I didn't change anything else : 
```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"mac"
EndSection

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#    Option		"CorePointer"
#EndSection

Section "InputDevice"
        Identifier  "mightymouse"
        Driver      "evdev"
        Option      "Device" "/dev/input/by-id/usb-Mitsumi_Electric_Apple_Optical_USB_Mouse-event-mouse"
        Option      "RelHWHEELOptions"      "invert"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
    Option      "SHMConfig"     "true"
	Option		"HorizEdgeScroll"	"0"
	Option		"VertEdgeScroll"	"0"
    Option      "TapButton1"    "0"
    Option      "TapButton2"    "3"
    Option      "TapButton3"    "2"
    Option      "RTCornerButton"    "0"
    Option      "RBCornerButton"    "0"
    Option      "LTCornerButton"    "0"
    Option      "LBCornerButton"    "0"
    Option      "VertTwoFingerScroll" "1" 
    Option      "HorizTwoFingerScroll" "1" 
EndSection

Section "Device"
	Identifier	"Configured Video Device"
    Option "FramebufferCompression" "off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
    SubSection "Display"
        Depth   24
        Virtual 2960    1280
    EndSubSection

EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
        InputDevice "mightymouse" "SendCoreEvents"
EndSection
```

I'm using a Macbook 2,1 if that makes any difference.

---

