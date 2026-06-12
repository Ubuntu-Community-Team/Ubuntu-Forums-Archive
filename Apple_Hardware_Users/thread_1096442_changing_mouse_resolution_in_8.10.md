---
title: "changing mouse resolution in 8.10"
date: 2009-03-14
forum: Apple Hardware Users
---

### Post by babucher on 2009-03-14
Greetings,

I've installed Ubuntu 8.10 on my Macbook Pro (4,1) dual-booting with OSX.  At this point I'm trying to figure out how to change the resolution of my mouse.  It's a Logitech Mx500.  It used to be that I could make the change in the xorg.conf file, but now it looks like it's handled through the new HAL system, and I'm somewhat lost.

I have figured out how to determine some information from xinput:

~$ xinput list

...

"B16_b_02 USB-PS/2 Optical Mouse"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

and, I've figured out how determine some of the more detailed information:
~$ xinput list-props "B16_b_02 USB-PS/2 Optical Mouse"
Device 'B16_b_02 USB-PS/2 Optical Mouse':
	Device Enabled:		1
	Middle Button Emulation:		2
	Middle Button Timeout:		50
	Wheel Emulation Inertia:		10
	Wheel Emulation:		0
	Wheel Emulation X Axis:		0, 0
	Wheel Emulation Y Axis:		4, 5
	Wheel Emulation Timeout:		200
	Wheel Emulation Button:		4
	Drag Lock Buttons:		0


But, at this point, I believe I'm supposed to create a .fdi file that contains the relevant information to adjust the Resolution, and this is where I'm stuck.  Any help would be appreciated.

---

### Post by cyberdork33 on 2009-03-15
I think you can put the same thing in the xorg.conf that you would have normally. the HAL interface is really for the touchpads.

---

