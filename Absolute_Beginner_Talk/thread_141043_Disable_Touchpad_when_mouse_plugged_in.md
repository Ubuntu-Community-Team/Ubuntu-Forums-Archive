---
title: "Disable Touchpad when mouse plugged in"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2006-03-07
Hey, is there any way i can disable my touchpad mouse when i have my mouse plugged in? it gets really annoying when im typing and i hit it by accident and i start typing at the start or even middle of what i was doing..

any advice, thank
~Lance

---

### Post by m.musashi on 2006-03-07
[QUOTE=noob_Lance]Hey, is there any way i can disable my touchpad mouse when i have my mouse plugged in? it gets really annoying when im typing and i hit it by accident and i start typing at the start or even middle of what i was doing..

any advice, thank
~Lance[/QUOTE]
Good question. That IS really annoying and I've never thought to ask that. I have problems with that in windows too. Some sort of script that detected the usb mouse and disabled the touchpad would be nice. I have no clue how to do that but someone out there probably does. As a short fix, you could "break" it by commenting out the driver or renaming it.

Look for this section or similar in your /etc/X11/xorg.conf
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
```
Try commenting it out and see what happens. You may need to reboot or log out and in for it take effect. This is just a thought. I've never tried it but I can't imagine it messing up too much.

Anyone else have any thoughts?

---

### Post by noob_Lance on 2006-03-07
i was thinkin maybe a script to kill the /dev/psaux and stsrt t us when the mouse is taken out... kind of a daemon script i guess.. if anyone knows how... it would be very appreciated. 

Thanks
~Lance

---

### Post by m.musashi on 2006-03-07
Yeah, that's beyond me. Sorry.

---

### Post by noob_Lance on 2006-03-07
lol beyond me too... someone here must kno how to do this.. anyone..  :S

---

### Post by m.musashi on 2006-03-07
Okay, did a little searching and found a couple threads that sort of address this. The first one looks promising.

[http://ubuntuforums.org/showthread.php?t=102604](http://ubuntuforums.org/showthread.php?t=102604)
[http://ubuntuforums.org/showthread.php?t=134865](http://ubuntuforums.org/showthread.php?t=134865)
[http://ubuntuforums.org/showthread.php?t=37860](http://ubuntuforums.org/showthread.php?t=37860)

EDIT: [This](http://ubuntuforums.org/showpost.php?p=581276&postcount=5) worked for me but I had to add ```
Option      "SHMConfig" "on"
``` to the xorg.conf to make it work. I don't know how to add the hotkey part. That would be quite close to automatic. The reference to the changelog sounds even better but I can't find anything on making that work like implied.

---

### Post by noob_Lance on 2006-03-07
i did that and got it working... now im tryin to make a bash script that will do this for me by prompt :p but no luck so far lol

---

### Post by m.musashi on 2006-03-08
If you get a script working, please share. I'd like something simpler. In the meantime, I'd like to figure out how to program hot keys. That would be the next easiest.

---

