---
title: "Stuck on 640x480 in Xubuntu"
date: 2007-05-21
forum: Apple PPC Users
---

### Post by macmini3399 on 2007-05-21
Hello,
I installed Xubuntu on my iBook G3, everything went well UNTIL i First booted into X. The display was stuck at 640x480. No other choices. Now 640x480 is WAY to big for my needs. Can anyone help me out here?

---

### Post by DaDave on 2007-05-21
Have you tried changing the display preferences (Settings > Display Settings)?

---

### Post by stmiller on 2007-05-21
Ah crap you may have to edit the file /etc/X11/xorg.conf

In a terminal, 

$ sudo gedit /etc/X11/xorg.conf

Make sure it has lines like this in the 'Screen' section:

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection

```


Save and close.

Then hit Cntl+Alt+Backspace[Delete key] 

to restart X.

---

### Post by gpi on 2007-05-21
Hi 

If that doesn't work,  try with default depth equal 16 instead of 24...

geoffroy

---

