---
title: "Microsoft Curve Keyboard Works in Bios but not GRUB"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by TheOnlyMerlin on 2008-01-29
I have a Microsoft Comfort Curve Keyboard 2000 that runs on USB.  It works just fine in the BIOS screen, and it works fine in Ubuntu and Windows also.  Although when it is in the GRUB menu, it does nothing.  Any thoughts?

-TheOnlyMerlin

PS I currently have my old and ugly ps/2 keyboard, it is just a massive pain to have both hooked up and have to pull the other out in order to switch to windows.

---

### Post by jeffus_il on 2008-01-29
> **TheOnlyMerlin said:**
> I have a Microsoft Comfort Curve Keyboard 2000 that runs on USB.  It works just fine in the BIOS screen, and it works fine in Ubuntu and Windows also.  Although when it is in the GRUB menu, it does nothing.  Any thoughts?

-TheOnlyMerlin

PS I currently have my old and ugly ps/2 keyboard, it is just a massive pain to have both hooked up and have to pull the other out in order to switch to windows.

I am guessing that grub does not have usb keyboard support, bios has and so does the kernel, which is loaded after grub, will look into it.

---

### Post by jeffus_il on 2008-01-29
Have you enabled usb keyboard support or legacy usb keyboard support in your bios?

---

### Post by The Cog on 2008-01-29
I have seen other complaints that Grub doesn't work with USB keyboards. I can't remember if there is a fix though. Maybe google for "grub usb keyboard"

---

### Post by jeffus_il on 2008-01-29
> **The Cog said:**
> I have seen other complaints that Grub doesn't work with USB keyboards. I can't remember if there is a fix though. Maybe google for "grub usb keyboard"
Bios enabling pops up.

---

### Post by TheOnlyMerlin on 2008-01-30
I went on my desktop that was having this problem and I checked the BIOS settings and as it turns out, USB legacy support was indeed off.  I turned it on, and GRUB recognized it.  

Strange that I actually used my USB keyboard to change those settings, but whatever.  I know there is an explanation, but it just seems odd.

Problem: Solved.

-TheOnlyMerlin

---

### Post by rmknowles on 2008-02-09
1.  BIOS has usb keyboard support, but it is supposed to relinquish control of the computer to a booting OS.  So, whatever process the BIOS is using to support the keyboard gets stopped after the BIOS gives control to GRUB.
2.  Apparently, GRUB does not support the usb keyboard (remember the OS and drivers haven't been loaded at this point).
3.  As the OS continues to boot, the usb keyboard driver loads and is available for the rest of the session.

I know this explanation is rough and simplistic, but that's why the keyboard works in the BIOS and the OS, but not GRUB.

Enabling usb legacy support should emulate a PS/2 keyboard, thereby mitigating the problem. :)

---

