---
title: "External monitor on a ThinkPad"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by flippy on 2007-03-21
Hi;

I've been searching but yet to find the answer(s) to the questions that I have regarding running an external monitor on my IBM Thinkpad A22M.

Here is my situation:
*Before changing over to Ubuntu, I was able to have an external monitor/projector attached to my laptop, usually running on the resolution of the laptop.
---->Now, I don't know why but I cannot seem to get my Acer widescreen monitor to work as an external monitor.
*I (from searching) found out that my looking at the xorg.conf file I can edit to make it work.
---->I'm looking at the file but cannot fully understand all the info. Here is what my xorg.conf looks like: (only part of the file)


Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

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

Section "DRI"
	Mode	0666
EndSection


*Also, before the change over to Ubuntu, I was running on a resolution of 1280x1024.
---->Even though I can change to that resolution the screen becomes partitioned and fuzzy. So, I'm stuck with the 1400x1050.


If any one can address these issues...thanks in advance.

---

### Post by annda on 2007-03-21
i have an nvidia card, which has a very good binary driver letting me configure almost anything i want with GUI, so i can't answer your questions directly. it **may** be that the resolution issue can be solved by changing the ati driver to fglrx:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

back up your xorg.conf file and make a note of what advices/posts you follow, so that you will be able to revert to a working configuration if anything goes very wrong. here are some interesting threads:

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)
[http://ubuntuforums.org/showthread.php?t=22412](http://ubuntuforums.org/showthread.php?t=22412)

this looks rather overwhelming at first, but after you read it and get your feet wet, it won't be that difficult to follow.

just to complete the list, here is a comprehensive xorg documentation:
[http://www.die.net/doc/linux/man/man5/xorg.conf.5.html](http://www.die.net/doc/linux/man/man5/xorg.conf.5.html)

post back to tell us how you are doing.

---

