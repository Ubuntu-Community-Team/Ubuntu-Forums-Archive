---
title: "Keyboard/Mouse Issues in Grub"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by imbzy on 2007-07-17
Hey everyone,
I have Ubuntu and Windows XP dual booted on this system, and everything has gone flawlessly for the past two days. However I believe when I connected my Webcam, something went wrong with the mouse and keyboard. The mouse wasn't responding after about ten minutes with Ubuntu up -- and this issue seemed to vanish as soon as I disconnected the Webcam -- and now the keyboard isn't working with Grub up even after I disconnected the Webcam, therefore I can no longer get into Windows.

I know there is a way to edit Grub so that Windows is top on the list in case I absolutely need to get into Windows (if anyone could explain how that would be great), but I still would like to have my keyboard working in Grub.

Currently the Webcam is disconnected and I'm hoping on my next restart that the issue will resolve itself.

(All devices listed above connect through USB)

Thanks.

---

### Post by bodhi.zazen on 2007-07-17
I am going to guess a hardware problem, possibly with your usb controller.

Try powering down (turn power off) and connecting your mouse/keyboard in various usb slots.

---

### Post by Rocket2DMn on 2007-07-17
Are you using your USB stuff through a hub?  If so, perhaps you overdrew the power to it and the hub shut off.  Also, not all computers enable the USB at startup, though you might be able to change a setting in your BIOS to activate USB on boot.

---

### Post by imbzy on 2007-07-17
> **Rocket2DMn said:**
> Are you using your USB stuff through a hub?  If so, perhaps you overdrew the power to it and the hub shut off.  Also, not all computers enable the USB at startup, though you might be able to change a setting in your BIOS to activate USB on boot.

Well the thing is EVERYTHING was working fine before I actually plugged in the Webcam. I could switch through Windows and Ubuntu with my keyboard.

I just tried opening the BIOS on startup and that wasn't working, leading me to believe that this is no longer a Grub issue. In fact, the lights on the keyboard only turn on as soon as I see the Ubuntu logo.

Would anyone know how I would go about turning this device on on startup?

EDIT: No hub. Going to try plugging my keyboard/mouse is different slots.
EDIT2: Using a different slot isn't working. Again, I really think my computer just isn't recognizing or "turning on" the keyboard on startup.
EDIT3: If this is a BIOS issue, I just don't get how a setting could be changed through plugging in a Webcam, or how I could fix this if I can't even get into BIOS being it requires a Keyboard..

---

### Post by Rocket2DMn on 2007-07-17
How old is your computer?
You can google your computer make/model and see if it's possible to enable the USB at startup, but if you can't, you can get your hands on these wonderful little green converters about the size of half your thumb that enable you to plug USB keyboards and mice into your computer's PS/2 ports.  They often come with USB mice and keyboards, I'm not even sure if you can buy them separately.

---

### Post by imbzy on 2007-07-17
> **Rocket2DMn said:**
> How old is your computer?
You can google your computer make/model and see if it's possible to enable the USB at startup, but if you can't, you can get your hands on these wonderful little green converters about the size of half your thumb that enable you to plug USB keyboards and mice into your computer's PS/2 ports.  They often come with USB mice and keyboards, I'm not even sure if you can buy them separately.

I believe I have a few of those on my old system. I'll have to check.

Computer is about exactly a year old. More or less it's a Gateway GT5034 that I've upgraded (PSU, video card).

I still don't get it. It SHOULD be able to "enable USB" since it worked before, and again I don't get why it just stops because of a Webcam.

I suppose if all else fails I could load up the recovery disc to reformat and see if that corrects the BIOS, but I rather not go through such extremities over something so simple.

EDIT: Okay, great! The PS/2 port worked, but I would still love to connect my keyboard directly -- would anyone happen to know how I could enable USB through the BIOS?

---

### Post by Rocket2DMn on 2007-07-17
Reformatting will not help your BIOS.
There should be something in the BIOS for USB Legacy Keyboard support.  Please have another look.  If you have a computer manual, you can refer to that.

---

### Post by imbzy on 2007-07-17
I'm pretty sure it would actually help. Recovery disc is not just a "Wipe windows, reinstall" -- it would turn it back to the way it was when I first got the machine, with the BIOS reinstalled/with default settings as well.

But thanks everyone for the advice and help!

---

### Post by Rocket2DMn on 2007-07-17
You should be able to reset the BIOS settings from within the BIOS.  There might be a few options for resetting like fail-safe or optimized.  Something like fail safe might disable some stuff (like ethernet), so be aware of that.  "Optimized" or "Factory Defaults" might be good if you have them.

---

