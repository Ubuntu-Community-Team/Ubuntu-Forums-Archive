---
title: "Using two mice in Ubuntu7.10"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by sx5622 on 2008-02-29
I was able to get the side buttons on my Logitech Mx518 to work (excellent), but I was using two mice before (I had them both plugged in at the same time) and now my other mouse (trackball) doesn't work. Any suggestions??

-Steve

I apologize for being an uber n00b.

Also, here is what my original xorg.conf looked like:


```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

```
Here is what I replaced it with:


```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Logitech USB-PS/2 Optical Mouse"
EndSection

```


THANKS!

---

### Post by forrestcupp on 2008-02-29
Did you actually have 2 mice working at the same time?  2 different pointers?

I have said for a long time that that would be beneficial and people thought I was crazy.  I didn't think it was possible.

---

### Post by sx5622 on 2008-02-29
> **forrestcupp said:**
> Did you actually have 2 mice working at the same time?  2 different pointers?

I have said for a long time that that would be beneficial and people thought I was crazy.  I didn't think it was possible.

No, I didn't have two pointers, but I had two USB mice plugged in my computer, and they both controlled the same pointer.  But now my trackball doesn't work.  I like the trackball, but I also like having my side keys binded on my MX518.  Perhaps I cannot have both.

---

### Post by waspbr on 2008-03-07
I have a Logitech  mx700 and mx1000, both "pugged"(wireless and bluetooth) in at the same time and they both work well. I haven't had any problems with any of them...

---

