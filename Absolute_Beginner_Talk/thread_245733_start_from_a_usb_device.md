---
title: "start from a usb device"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by patber on 2006-08-28
After determing that my laptop cannot boot from a USB device, it should be possible to boot from the liveCD and then specify that I want it to start from the USB device, so I would really like some tips on how to enable this setup.

Cheers,
pb

---

### Post by Metacarpal on 2006-08-28
Hi pb,

I want to make sure I'm understanding your problem.

1. You checked your computer's BIOS settings, and it cannot be set to boot from a USB device, correct?

2. You wish to install Ubuntu to said USB device using the LiveCD, correct?

3. When you run the LiveCD, the USB device appears on the desktop, correct?

4. You wish to set up the bootloader (GRUB) so that it points to your USB device to start Ubuntu, correct?

5. This a dual-boot setup you're trying to acheive (that is, Windows on the hard drive, Ubuntu on the USB, and you can choose which to load), correct?

If I'm mistaken about any of that, please let me know.  The more detail you can provide, the easier it will be to find a solution for you. :)

---

### Post by patber on 2006-08-29
hi,
1 - Yes

2 - Already done

3 - Yes, /dev/sd1

4 - Yes, I would like to be able to start Ubuntu from the USB drive

5 - Yes

Thx a lot for any help on doing this the easiest way

pb

---

### Post by PaulFXH on 2006-08-29
I've used this guide to boot four different Linux distros (including Ubuntu Dapper and Breezy) from a "non-bootable" usb hd ([https://help.ubuntu.com/community/BootFromUSB)](https://help.ubuntu.com/community/BootFromUSB)).

---

### Post by mssever on 2006-08-29
> **PaulFXH said:**
> I've used this guide to boot four different Linux distros (including Ubuntu Dapper and Breezy) from a "non-bootable" usb hd ([https://help.ubuntu.com/community/BootFromUSB)]("https://help.ubuntu.com/community/BootFromUSB%29").
Oops...the closing parenthesis somehow became a part of the link. Try [this one]("https://help.ubuntu.com/community/BootFromUSB") instead.

---

### Post by patber on 2006-08-29
great I will take a look, but bascilly what I would like to be able to do is:
Just insert a cd in cd-rom drive and have it boot into the USB drive where I have Ubuntu installed.

---

### Post by PaulFXH on 2006-08-29
Well, if you dual-boot with grub (or anything else) you must go through the boot menu.
However, I don't believe this can be described as an inconvenience.
If, OTOH, you just want to single boot Ubuntu from a usb hd, the link I suggested (thanks to mssever for spotting the deliberate error :D ) will explain exactly what you need.

---

