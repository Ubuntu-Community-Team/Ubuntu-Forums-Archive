---
title: "[SOLVED] Tried dual monitor setup and I think X11 is toast."
date: 2008-04-04
forum: Apple Intel Users
---

### Post by pyjimbo on 2008-04-04
I tried getting dual monitors to work on my Intel Mac and I can no longer read the screen. It cut off and is all scratchy seeing sextuple like when a boxer gets punched. I have six mice on the screen and I have to play a little game to guess which one is the real one.

:lolflag:

I had no idea that doing dual monitors on the Intel Mac had separate instructions, **so I was oblivious.**

How can I get X11 back to just the Mac LCD and one monitor? I don't want it to look for the Sony Trinitron E-200.

I imagine I would need to post the X11 org files here but I would need to figure out how to get files onto a thumbdrive at the command line. I am a little familiar with nano.

To make this more enticing I can't wipe it because there is a CD stuck in the drive. It won't come out and is scheduled for repair. This happened while in Mac OS X 10.4.11.

---

### Post by cyberdork33 on 2008-04-04
what happens when you disconnect the other monitor?

---

### Post by pyjimbo on 2008-04-04
> **cyberdork33 said:**
> what happens when you disconnect the other monitor?

It goes through the boot process as normal but then displays a series of items with [OK] on the left hand side of the screen. It gets to * Running local boot scripts (/etc/rc.local) [OK] and the screen flashes three times, then it sits there with a blinking cursor underneath it.

When I hit the power button it says * Stopping Gnome Display Manager...

This unit works good on the Mac OS side of things in case anyone is wondering about the hardware itself, seems to be in good order minus the CD drive.

---

### Post by AustinC on 2008-04-04
try logging in at the console and then type "startx"
it should give you some sort of error message at least.

---

### Post by pyjimbo on 2008-04-04
> **AustinC said:**
> try logging in at the console and then type "startx"
it should give you some sort of error message at least.

Fatal server error:
no screens found
XI0: fatal IO error 104 (Connection reset by peer) on x server ":0.0"
after 0 requests (o known processed) with 0 events remaining

---

### Post by cyberdork33 on 2008-04-05
after Xorg fails with the one monitor attached, use CTRL+ALT+F1 to get to a terminal login.

run```
sudo dpkg-reconfigure -phigh xserver-xorg
```then restart

---

### Post by pyjimbo on 2008-04-05
> **cyberdork33 said:**
> after Xorg fails with the one monitor attached, use CTRL+ALT+F1 to get to a terminal login.

run```
sudo dpkg-reconfigure -phigh xserver-xorg
```then restart

The troubleshooting in this thread was great, thank you both. :KS

The shortcut needs one more key fn+CTRL+ALT+F1 otherwise F1 is brightness adjustment.

---

### Post by cyberdork33 on 2008-04-05
> **pyjimbo said:**
> The troubleshooting in this thread was great, thank you both. :KS

The shortcut needs one more key fn+CTRL+ALT+F1 otherwise F1 is brightness adjustment.
No it is because F1 is not F1 on your keyboard unless you are holding Fn. a Normal full keyboard has no Fn key.

---

