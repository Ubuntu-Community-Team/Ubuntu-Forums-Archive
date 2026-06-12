---
title: "Macbook 2,1 Ubuntu 10.04 Keybaord"
date: 2010-05-06
forum: Apple Hardware Users
---

### Post by bacord on 2010-05-06
Running rEFit to dual boot snow leopard and Ubuntu 10.04.  I have a black macbook 2,1 model.  I have searched everywhere for a guide for this model and have not had any success.  For the most part I have been able to configure everything from other guides.  I get the following error when trying to change the keyboard to the Mac layout (in order deadkey alt and make the Command or Apple key the major key).  Does anyone have any suggestions?  Is there any more info I can provide?  Thanks.

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10706000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by damagu on 2010-06-12
Getting the same error on my Macbook Pro 3,1 when running Ubuntu 10.04. I want the ctrl key mapped to the Command/Win/Apple key and vice versa so that I have the same behaviour as I have in Mac OS. So you hit the Apple key to get the Ctrl function and the Ctrl key to get the Super function. 

Trying to do anything with the keyboard options or trying to do anything with xmodmap results in the error:

[FONT="Courier New"]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10706000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd [/FONT]

I see that a bug has been recorded already but is there anything we can do to get around it?

Thanks

---

### Post by damagu on 2010-06-22
Does anyone know what to do about this error?

---

### Post by AmaranthineNight on 2010-07-13
I had this problem, and after changing my keyboard layout from "USA (Macintosh)" to "USA" I was able to enable the Macbook/MacbookPro keyboard model without an error, but it had no effect on the behavior I'm looking to change (swap the apple key with ctrl).

Any ideas?

---

### Post by linuxopjemac on 2010-07-13
seems like a bug
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/596652](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/596652)

---

### Post by damagu on 2010-08-19
> **AmaranthineNight said:**
> I had this problem, and after changing my keyboard layout from "USA (Macintosh)" to "USA" I was able to enable the Macbook/MacbookPro keyboard model without an error, but it had no effect on the behavior I'm looking to change (swap the apple key with ctrl).

Any ideas?

Everything I've tried works temporarily at best. In the end I gave up and learnt to use it the "normal" non-mac way.

:-(

---

