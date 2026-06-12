---
title: "Booting from CD on Dell Inspiron 1300"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by monkeytypist on 2007-02-15
Hello, I'm very keen to try Linux although/because I know practically nothing about it.

To that end, I have a 6.10 CD that I got with a magazine.

I want to do the live test off CD, but every time I reboot with my CD in the drive, it goes straight into Windows.

Is there some setting I need to change. . .?

---

### Post by FyreBrand on 2007-02-15
> **monkeytypist said:**
> Hello, I'm very keen to try Linux although/because I know practically nothing about it.

To that end, I have a 6.10 CD that I got with a magazine.

I want to do the live test off CD, but every time I reboot with my CD in the drive, it goes straight into Windows.

Is there some setting I need to change. . .?You are probably going to have to enable booting from CD/DVD in your computers BIOS.  Are you comfortable doing that?

You might be able to avoid this if the computer permits boot options via a bypass key.  This isn't very common so it might not apply to you.  Very early one (like the first 2 or 3 seconds) in the boot process a message telling you to press key <name> to boot from CD would appear if the option is available.  You would have to press the key then.  If it's not available you will have to change your BIOS settings to allow a boot from CD.

---

### Post by monkeytypist on 2007-02-15
> **FyreBrand said:**
> You are probably going to have to enable booting from CD/DVD in your computers BIOS.  Are you comfortable doing that?

You might be able to avoid this if the computer permits boot options via a bypass key.  This isn't very common so it might not apply to you.  Very early one (like the first 2 or 3 seconds) in the boot process a message telling you to press key <name> to boot from CD would appear if the option is available.  You would have to press the key then.  If it's not available you will have to change your BIOS settings to allow a boot from CD.

I was afraid you'd say that :/.  i386, how do I reconfig BIOS settings?

---

### Post by FyreBrand on 2007-02-15
Is the computer a 386 or a Pentium III?  What version of Windows is running on it?

To get into the BIOS there will be a key you have to press right at boot time shortly after turning the power on.  On many computers it's F2 or the "Delete" key.  It normally flashes this message at boot time.  A BIOS version message pops up and then a message saying something similar to "Press F2 to enter setup at this time."

Changing BIOS settings can make your computer inoperable so only change them if you are sure about the selection.  It's not going to hurt anything to look but don't save your changes unless your are certain about them.

There are lots of different BIOS versions.  It would be good to read a bit about your BIOS from your motherboard vendors website.  If the stuff you see in the BIOS makes sense then you can proceed on your own, if not then it would be a good time to get friend over and look with you.

The main section you're looking for in the BIOS settings is the Boot section.  This lists the devices (hard drive, cd drive, floppy, usb, network) that the computer can boot to.  One of the menus is usually a "boot order" menu.  In this area you would want to enable booting form CD Drives (often labeled as Optical Drive or the actual CD drive vendor name and model like Sony CDR-1234).   There could also be a boot order list in the BIOS.  This is where the computer choose the order of the devices in which to boot.  The hard drive is probably first on that list.  You would want to make the CD/DVD drive first on the list.

I hope that helps some.

---

### Post by chimpus on 2007-02-17
> **monkeytypist said:**
> Hello, I'm very keen to try Linux although/because I know practically nothing about it.

To that end, I have a 6.10 CD that I got with a magazine.

I want to do the live test off CD, but every time I reboot with my CD in the drive, it goes straight into Windows.

Is there some setting I need to change. . .?


On many Dell PC's you have to press the F12 key when it first boots up (DELL POST Screen) This will bring up the boot menu were you can choose CD for boot. I'm sure this is the issue.

---

### Post by sabertooth_cat on 2007-02-17
You might have to hold the F12 key down while quickly tapping the "down" arrow in order to see a menu to choose where you want to boot from. When you see the choices, tap the up/down arrow until it is highlighting the choice you want. Next, let go of the F12 key and press "enter" if it doesn't start booting.

---

