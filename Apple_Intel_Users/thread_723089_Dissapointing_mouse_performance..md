---
title: "Dissapointing mouse performance."
date: 2008-03-13
forum: Apple Intel Users
---

### Post by PaulFXH on 2008-03-13
The 6 y-o roller-ball two-button PS2 mouse on my Dell desktop works quite a bit better than the relatively new usb optical Mighty Mouse on the MacBook.
(Looking at Ubuntu Gutsy on both machines).
Strangely the /etc/X11/xorg.conf section for Mouse is exactly the same on both computers:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```
Now the Mighty Mouse doesn't have a PS2 conection and doesn't need 3-button emulation. So, it seems strange that it still has the above in its xorg.conf.
Nevertheless, in trawling through this section of the forum ,  I see that many people have the very same Mouse section in xorg.conf on the MacBook.
So, is this appropriate for a MacBook?
If so, what else can I do to make the mouse in Ubuntu/Mac more responsive?

---

### Post by cyberdork33 on 2008-03-13
The protocol is still right even though it is through a USB connection. I don't think you need the emulate3 buttons... That is added standard though I think, because it doesn't hurt anything.

As far as getting it work work better, you probably need to add some more button functions, and definitions for side scrolling.


See this thread:
[http://ubuntuforums.org/showthread.php?t=223576](http://ubuntuforums.org/showthread.php?t=223576)

---

### Post by PaulFXH on 2008-03-13
Thanks for your reply.
OK, I tried the revised Mouse section in/etc/X11/xorg.conf.
However, I found that on attempting to reboot that Ubuntu wouldn't boot on my MacBook -- just stopped right in the middle and wouldn't go any further. Didn't even go to a shell.
So, had to go into one of my other OSes and get the older Mouse section (commented out) back.
Don't at all understand why it wouldn't boot. Perhaps has something to do with the different mouse driver although that does seem to be present on my system.

Nevertheless, even if it had booted, I'm not sure this would have resolved my problem as this new Mouse Section seemed more concerned with getting all of the Mighty Mouse buttons to work.
My problem is perhaps a little more fundamental in that I really just want the pointer (arrow) to always go in the same direction in which the mouse is moved.
This really doesn't happen reliably as things stand now.

---

