---
title: "Here is how to get Thinkpad scroll and NO middle PASTE!"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-09-06
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option "YAxisMapping" "4 5"
    	#Option "XAxisMapping" "11 12"
    	#Option "Emulate3Buttons"
    	#Option "Emulate3Timeout" "50"
	Option "ButtonMapping" "1 9 3 4 5 6 7 8 2"
    	Option "EmulateWheelButton" "9"
    	Option "EmulateWheel" "true"
EndSection

It took me a while, but you must remap physical button number two (mniddle) to button 9.
Then you emulate wheel based on the imaginary button 9 (logical). While it appears that middle paste only looks for Logical button 2, where emulate wheel will look for what you tell it to!

Now if we can just get HORIZONTAL scrolling to work! I really tried, mapping the x-axis to different numbers and it seems I exhausted all possibilites without any sucess.

---

### Post by asmoore82 on 2007-09-06
Thinkpad T42 here and there is an undocumented scroll wheel on the far left edge of the touchpad.

---

### Post by systemintheglitch on 2007-09-07
Hmmm..
You might need to acount for that in the button mapping..

---

### Post by Mr.Beast on 2007-09-07
Many thanks for this info, it's been bugging me as well.

The undocumented scroll feature seems to be for the T series in general and seems to work "out the box". I just tried it without the above modifications and it works fine (for vertical scrolling)
Personally, I'm a trackpoint kinda guy and normally disable the touchpad to reduce erroneous mouse action, however I may well leave it on now, with the scroll feature.

It would be useful if systemintheglitch, or others could put some info on the location of the file that would need to be changed and edited though :-) 
Thanks guys.

---

### Post by systemintheglitch on 2007-09-07
Whoops!!

/etc/X11/xorg.conf

Find the section for a mouse, that has stuff like that in it!

Sorry thats the best I could do.

Also, always back up xorg.conf before messing around!

---

### Post by upforthedownstroke on 2008-03-04
thank you so much for this; all the other xorg fixes i'd found hadn't worked right.

---

### Post by alexei.colin on 2008-05-29
Thank you so much! Smoothly scrolling away without pasting random stuff from clipboard -- you saved us all a lot of frustration!!

---

