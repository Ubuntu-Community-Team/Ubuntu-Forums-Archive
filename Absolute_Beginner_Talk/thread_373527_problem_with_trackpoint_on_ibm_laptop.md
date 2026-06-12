---
title: "problem with trackpoint on ibm laptop"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by dedmonds on 2007-03-01
Hello,

I have installed Ubuntu 6.10 on an IBM ThinkPad T22 laptop. The installation went smoothly in general. However, I have not been able to get the TrackPoint mouse and buttons to work properly. An external PS2 mouse works properly (including the scroll button functionality). The TrackPoint hardware does work correctly under WinXP. I am not sure how to get the TrackPoint mouse to work in Ubuntu.

I believe the problem may be due to incorrect settings in the xorg.conf file based on similar issues that others have had, but I have not been able to get this to work. I thought someone here might be able to help me sort this out faster than I will be able to on my own. Any help you may be able to provide would be greatly appreciated.

Thanks,
Duane

---

### Post by ubu fubar on 2007-03-01
Are you talking about the little red nipple on the keyboard, or the buttons around the touchpad, or the ensemble? Have a look at the ThinkWiki site, specifically the pages on the [UltraNav]("http://www.thinkwiki.org/wiki/UltraNav") and the [TrackPoint]("http://www.thinkwiki.org/wiki/TrackPoint"). With their help I was able to get almost all of the buttons on my T30 working fine under Gnome.

Here's the relevant sections from my xorg.conf:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SHMConfig"	"true"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

```

```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by desheikh on 2007-03-01
On my laptop the synaptic settings are never created after an install. I just regenerate the xorg.conf file
 
sudo dpkg-reconfigure xserver-xorg 

and the proper settings are automatically added.

---

### Post by dedmonds on 2007-03-01
Yes, I am having problems with both the red nipple and the three buttons on the laptop just below the nipple. None of these is working currently. Thanks for the advice and the links. I will see if this gives me enough information to correct the problem when I get back to the house tonight.

---

### Post by dedmonds on 2007-03-01
I made changes to the xorg.conf configuration file to make it agree with the parts listed above, and the TrackPoint nipple and all buttons are now fully functional. Thank you very much for your help. You guys are great.

---

### Post by dedmonds on 2007-03-02
I just noticed that if I boot the computer with an external PS2 mouse plugged in, the TrackPoint inputs do not work. However, if I unplug the external mouse until the computer boots to the login screen, the TrackPoint inputs work fine (even after I plug in the external mouse).

Do you have any idea why this is the case?

---

