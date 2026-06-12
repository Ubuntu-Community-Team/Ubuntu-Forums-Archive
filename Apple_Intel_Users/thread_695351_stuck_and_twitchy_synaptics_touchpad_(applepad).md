---
title: "stuck and twitchy synaptics touchpad (applepad)"
date: 2008-02-12
forum: Apple Intel Users
---

### Post by aztechclan on 2008-02-12
Hi,
I'm runny Gusty on a new v3 apple macbook pro.  I have experienced a problem when using the touchpad/keyboard where my cursor will get stuck moving in a certain direction and I can't stop it or use the keyboard.  I'm using pommed and also 'syndaemon -t -d'.  Restarting gdm from an ssh console gets me going again, but I loose all my programs ..  Removing the modules applepad, xpad and some others didn't help, nor did plugging in other usb keyboards and mice.  The cursor still just jerks in one direction constantly.

Anyone know what causes this or how I can fix?  It's some kind of fat-finger keyboard+touchpad combo that sets it off.  I am going to try 'syndaemon -d -i 1 -k' even though it's annoyingly slow switching.

---

### Post by cyberdork33 on 2008-02-13
The touchpad's hardware layer module is appletouch, not applepad.
There have always been odd behavior with the touchpads on Mactels, but yours sounds very odd. Still, might try the synaptics tutorial in the FAQ, there are some posted configurations that seem to tame the touchpads for many people.

---

### Post by aztechclan on 2008-02-13
Now that I'm using the following it hasn't happened after about 8 hours of continuous use.  I'd say this is a good solution, it makes you wait 1 second between switching from typing to touchpad.

syndaemon -d -i 1 -k

I will post back here if the problem happens while using this to let you guys know.  Again it was somewhat rare (once a day while using touchpad), but when it happened everything had better be saved out to disk . :(

---

