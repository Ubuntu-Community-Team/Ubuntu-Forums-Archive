---
title: "Logitech G5 Gaming Mouse buttons..."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by neoMAX on 2008-03-13
Okay, so I'm in firefox, and I want the back button to move the browser back a page like normal. I also want the tilt wheel to behave properly (at the moment left goes forward a page and right goes back a page - weird). I would also like to see middle click function like autoscroll if possible.

I've googled a good hour and found many pages saying to edit xorg.conf and I've done all these but none of the procedures seem to change anything after reboot.

---

### Post by neoMAX on 2008-03-13
Bump...!

---

### Post by Daveth on 2008-03-13
so, does your xorg.conf look like this:

Re: How do I make my G5 buttons work? 

Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "auto"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7 4 5 6

from
[http://ubuntuforums.org/showthread.php?t=715536&highlight=logitech+mouse](http://ubuntuforums.org/showthread.php?t=715536&highlight=logitech+mouse)
?? That post fixed most of the button issues. You are saving the file after you edited it, aren't you?

---

### Post by neoMAX on 2008-03-13
Here's what's in my xorg.conf:

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "evdev"
	Option "CorePointer"
	Option "Name" "Logitech USB Gaming Mouse"
	Option "Device" "/dev/input/event1"
	Option "ZAxisMapping" "4 5 6 7"
	Option "Emulate3Buttons" "false"
EndSection

EDIT: The post you made fixed it. Thanks!

---

### Post by Daveth on 2008-03-15
excellent!

---

