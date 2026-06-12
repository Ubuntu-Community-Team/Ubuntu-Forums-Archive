---
title: "Logitech V200 Mouse"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by snapcase16 on 2006-08-29
I've been trying to install this mouse for the past couple hours. I started out by attempting to follow the steps described at [http://www.ubuntuforums.org/showthread.php?t=219894](http://www.ubuntuforums.org/showthread.php?t=219894). When that failed, I improvised. I added a udev rule: 

KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/event4". 

I then modified my xorg.conf file:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"            "usb-0000:00:1d.7-6.2/input0"
	Option		"Device"	        "/dev/input/event4"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

This setup allowed me to boot Ubuntu without bothering X. However, when I would attempt to use the mouse, the pointer would fly all over the screen and open random programs. I restored my original xorg.conf file and lowered the sensitivity and speed mouse settings, but the same problem occurred when I booted with the modified file. Does anyone know how to remedy this? Thanks for any possible help.

---

### Post by cokhavim on 2006-08-29
I got my V200 working using that how-to link in your post (only section 1).  My xorg.conf and udev are the same as those in that link, except with "Logitech USB Receiver" in the udev.

But now, the tilt-wheel left and right buttons are reversed.  It's very annoying.  Any ideas?

---

### Post by snapcase16 on 2006-08-29
I wish that I could help you out, but my experience with Linux is rather limited. I tried the instructions on that page again and I got lucky. Even though you're supposed to be able to use any event numbering between 4 and 9, event 4 does not. Event 9 definitely does. Thanks.

---

### Post by cokhavim on 2006-08-29
Well, I found the answer to the left and right tilt wheel mix up.  I edited the relevant section in my xorg.conf to this:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/event9"
        Option          "HWHEELRelativeAxisButtons"     "7 6"
EndSection

yay.

---

### Post by Jeroen Vernooij on 2006-08-29
Hmm this is very strange, I have a Logitech V200 and all I did to get it to work under Dapper, is inserting the receiver in an USB-port, and boot dapper. Everything works (even at first login-screen at first boot!)

---

### Post by cokhavim on 2006-08-29
yeah, it also worked for me when i first plugged it in, but the left-tilt and right-tilt didn't work for me until i did all the above.

---

### Post by oLdsk3wL on 2006-10-05
for me the mouse works under dapper and now under edgy beta. I just plugged it in and it worked.

but I didnt get the wheel buttons working. have anyone an idea? or a tip? I want to use all 5 buttons, the left, the right and the middle button are already working.

---

