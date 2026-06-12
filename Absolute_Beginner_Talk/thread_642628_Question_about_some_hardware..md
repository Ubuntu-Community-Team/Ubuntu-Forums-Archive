---
title: "Question about some hardware."
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by pankirk on 2007-12-16
Ok I am looking to get a couple things this month, and I just want to know if they will work with linux ubuntu 7.10 64 bit. They are as follows: A USB keyboard, a USB mouse, a TV tuner, and maybe a device that will let me play console games on my computer monitor. Also I dont really know what kind of TV tuner will work with linux ubuntu 7.10 64 bit, so maybe someone can tell me one that will work with it. Also, maybe someone can tell me if a USB mouse and USB keyboard will work with ubuntu 7.10 64 bit aswell, I dont need help finding these because Im sure that all USB keyboards, mouses work the same... Ok thanks in advance for anyones help!

---

### Post by Existentialist on 2007-12-16
All standard keyboards and mice should work with Ubuntu.  There may be some obscure brand of them with unusual shortcut keys that would not be assigned by default, but for the most part I doubt you will have any problems with any USB keyboard or mouse.  As for the TV card, I'll let somebody with more experience comment on which ones have drivers easily available for Ubuntu.

---

### Post by pankirk on 2007-12-16
Thank you! I figured that they all would work mostly the same. I will probably get a logitech 5 button laser mouse one, hopefully all 5 buttons will work.

---

### Post by Existentialist on 2007-12-16
I have a logitech 5 button, and I am used to using the two side buttons as forward and back for web browsing which does not work by default in Ubuntu.  I had to change my xorg.conf:

>sudo nano /etc/X11/xorg.conf

And changed:

Section "InputDevice"
	[INDENT]Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
        Option "Device" "/dev/input/mice"
	Option "Protocol" "ExplorerPS/2"
	Option "Emulate3Buttons"       "true"[/INDENT]
EndSection

To:

Section "InputDevice"
   [INDENT] Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "**4 5**"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "**1 2 3 6 7**"[/INDENT]
EndSection

The parts in bold may be different for you, I think for my friends it was:

    Option         "ZAxisMapping" "6 7"
    Option         "ButtonMapping" "1 2 3 4 5"

Just backup the old xorg.conf before making any changes in case it is any different for you if you decide to try any of this.

---

### Post by pankirk on 2007-12-16
Oh thanks, I will actually have to try that out now because the mouse I have has 5 buttons. Thanks again!

Also, do I have to restart once I edit the xorg.conf?

Because I just did it and it does not work....

This is mine 

> 
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option 		"Buttons" "7"
	Option 		"ButtonMapping" "1 2 3 6 7"


im pretty sure i did it right? it was this

> 
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"


---

### Post by Existentialist on 2007-12-16
You only need to restart x (ctrl+alt+backspace) after saving it.  This will kill your open processes like firefox so save what you are doing just in case.

---

### Post by pankirk on 2007-12-16
Oh thanks. I was wondering why it wasnt working. I will have to restart later, because I am uploading a video to youtube. But you are sure I did everything right? My current mouse is only 5 buttons (left click, right click, middle, and 2 side buttons.) Hopefully It will work when I restart. Anyway, I really do appreciate your help! Thank you again!

---

### Post by halitech on 2007-12-16
for the tv tuner card, most seem to have the best of luck with the hauppage cards, I have an Asus My cinema card which partly works but wouldn't recommend it even though it is cheap.

---

### Post by Existentialist on 2007-12-16
If it doesn't work like that or by changing the numbers in the parts I mentioned, I seem to remember changing the line:

Option "Protocol" "ImPS/2"

To:

Option "Protocol" "ExplorerPS/2"

I don't know if this was related to this but I did find this guide which says essentially says what I said.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox)

---

