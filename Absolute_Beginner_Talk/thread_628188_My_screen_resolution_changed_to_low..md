---
title: "My screen resolution changed to low."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Ronjr on 2007-12-01
Ok, I tried to fix my mouse problem [here]("http://ubuntuforums.org/showthread.php?t=219894&highlight=mouseman") . I restarted the PC and before it logged back in a pop up box came up and said it was loading in low resolution or something like that. Anyways the highest resolution my screen will goto is 800 x 600. I'm just curious what happened and how can I fix this?

Here's exactly what I did.


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"	"Micro$oft Micro$oft intellimouse"   This is the name thats in here: cat /proc/bus/input/devices
EndSection



After that I typed this: sudo /etc/init.d/udev restart

Then ctrl + alt + backspace - and the computer restarted and gave me the low res window after reboot.

BTW I'm only 2 days into ubuntu so I am still very new.

Thanks in advance!!!

---

### Post by Ronjr on 2007-12-01
Ok, well i went into screen and resolution and fixed the settings. I would still like to know what happened even though I might not understand it.

Also how can I get the forward and back button to work on my mouse?

---

### Post by r00tzz on 2007-12-01
I have the same problem when I configure a mouse using the evdev driver, but the mouse is not connected to the computer. 

Even after pluging in the mouse X was messed. Now I have backed up 2 different confs to X.

---

### Post by Ronjr on 2007-12-02
Anybody have any suggestion?

---

### Post by r00tzz on 2007-12-10
<joke> Maybe you have Microsoft spelled wrong in your xorg.conf </joke>

Seriously, I don't think evdev is that stable yet. Try reconfigure using the "mouse" driver.

---

