---
title: "change keyboard without working keyboard or prevention possible?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by pixelstuff on 2007-03-26
hello
my usb keyboard seems to be dying - i am having troubles both on xp and the ubuntu partions for a few days. Just before I thought now its gone for sure but I was able to get it working again - the last time? When I plugged another keyboard on thekeyport-port  and rebooted the PC it did not recognize it and I wonder how will I edit the xorg without a keyboard? I can't even log in or choose another OS during booting. Can I prevent that from happing the next time with a "failsave" keyboard entry? 
At the moment I have this in my xorg.cong:
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc102"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"

mouse and keyboard belong to the same usb device, it is one product

:) thank you very much!!

---

