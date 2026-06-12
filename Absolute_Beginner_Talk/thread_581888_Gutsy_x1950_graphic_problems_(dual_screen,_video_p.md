---
title: "Gutsy x1950 graphic problems (dual screen, video playback)"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-10-19
I just made a clean install of Gutsy Gibbons AMD64 version on my computer that has an ATI Radeon x1950 / R580 video card.  From what I've [read]("https://help.ubuntu.com/community/RadeonDriver"), I can only use the proprietary drivers with this video card.

The biggest problems right now are:
1) I can't extend my desktop to the 2nd monitor.
2) Compiz won't work, error: "Composite extension is not available."
3) Their are color problems for all videos I play regardless of the encoding.

Are these problems resulting from the ATI's proprietary drivers?  I have Gutsy Gibbon running just fine on my laptop (Dell Inspiron 6000, Mobile Radeon 300) but not on my desktop. :(

---

### Post by Vonnegut on 2007-10-20
The problem with composite can be fixed by editing the xorg.conf file in //ect/X11/. 

```
cd //etc/X11
```

```
sudo gedit xorg.conf
```

Then, scroll to the bottom of the file. You'll see 

> 

Section "Extensions"
	Option		"Composite"	"SOMETHING, either disable or 0 or something bad :(" 
EndSection



Change the "SOMETIHNG" to "1" or "Enable"

This should fix up that problem. Post here if it does!

---

