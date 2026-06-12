---
title: "Slow scrolling on Dell 700m"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by colinz on 2006-12-24
Hi, I just installed edgy on my Dell 700m, and I am experiencing slow scrolling and dragging windows.  Using lspci, I get:

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

But under my xorg.conf, I get 

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Does that mean my graphic card is not properly installed? where can I get a driver update? Thank you!

---

### Post by MkfIbK7a on 2006-12-24
depends what graphic card you have you may not need to install anything what graphics card do you have?

---

### Post by colinz on 2006-12-25
mine is intel 855GM integrated graphic card.

---

