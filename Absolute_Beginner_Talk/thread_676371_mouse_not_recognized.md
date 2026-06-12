---
title: "mouse not recognized"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by steven448 on 2008-01-23
Hello-
i just installed Ubuntu.
(ASUS KM400A motherboard)

Ubuntu does not recognize my mouse.. just an old 2 button mouse on a serial port.

I tried to run mouseconfig, but it won't run unless i log in as ROOT (right?).
Is there a default password for ROOT? 
 
Thanks

---

### Post by Bubba64 on 2008-01-23
Sometimes a restart will fix this I suspect you have tried this already not having control over the mouse may make it hard to do a restart, I don't know how to due this without a mouse. You can restart your x by holding down crtl-alt the hitting backspace. Check for other options if you can.

---

### Post by steven448 on 2008-01-23
Okay- I figured out how to login as root... when logged in as a user, you have to change your administrative priv.'s by going to System --> administrate --> Users & Groups, then check off the option to allow yourself to SU.
But still I can't run mouseconfig, I'm wondering if perhaps it's not included in the base install??

Bubba- I'll try that idea of restarting X; thanks.

EDIT: I'm back.. tried restarting X, that didn't work.

---

### Post by uflieven on 2008-02-02
The following solution works certainly in Ubuntu 7.04 or older.
I don't know if it works in 7.10, and it doesn't work in 8.04 (4th alpha release)

You should go to terminal, then type:
**sudo nano /etc/X11/xorg.conf**
In that file, some lines down, you will find a section about the mouse.
Change **/dev/input/mice** to **/dev/ttyS0** or **/dev/ttyS1** (the S must be a captial letter, followed by a zero or a one (zero if your mouse is connected to the first serial port, one if it's connected to the second)
In the line underneath, you'll find something like **"ExplorerPS2"**
Change that to**"Microsoft"**
Press CTRL+X, say yes when asked to save and reboot.
Afterwards, your mouse should be working.
I also have a serial mouse, and in the past it worked flawlessly.

I have one question though, has anyone here a solution for Hardy (8.04)?
The xorg.conf file in 8.04 is very short, and i can't find the right option, to get my serial mouse working.

Update: fixed, found a solution for 8.04:

Under the mouse section, add the following lines:
[B]Option    "Device"     "/dev/ttyS1"
Option    "Protocol"   "Microsoft"[/B]

If your mouse is connected to the first serial port, use **/dev/ttyS0** instead.

---

