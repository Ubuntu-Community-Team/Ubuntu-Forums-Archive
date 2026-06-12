---
title: "How to go back to former video card installation?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-10-24
I just updated to Gutsy and it installed a new (propietary) driver for my ati card. Now it crashes often into black screens. How can I get back to the old configuration?

Any answer welcome! Ubuntu is impossible to work with now!! I really need it!!

---

### Post by Sturmeh on 2007-10-24
if u can get into terminal using ( ALT+CTRL+F2 ) login then...

type: "sudo nano /etc/X11/xorg.conf" ( use gedit if you manage to start x )

Find the "DEVICE" section, and

> Section "Device"
	Identifier	"GFX NAME"
	Driver		"driverhere"

find that, and swap whateva driver there is, for "ati" which should fix some problems. ( You may also have to remove the propietry driver from under "Restricted Driver Management" )
[B]
EDIT:[/B] Or swap in "vesa" if all else fails, it's a basic driver for any card, afaik.

Good luck!

---

