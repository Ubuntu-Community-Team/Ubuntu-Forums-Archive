---
title: "USB freezes ubuntu"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by ccaaee on 2007-01-20
Hello all

I am having problems with USB devices on Edgy and Dapper

This concerns at least usb pen drives, and usb adsl modems.

The PC is pIII based and the usb controller is:

USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 

If I plug a usb device in before booting all is OK.  If I plug it in after booting the computer hangs.
I tried a " tail -f /var/log/messages" before plugging the device in but that reports nothing and of course as the computer has hung and therefore requires a hard reset there is no way of looking at what might have caused this...

I've thought of irq issues but don't know how to test this

Any Ideas?

ccaaee

---

### Post by riven0 on 2007-01-21
If you really think it's related to an IRQ conflict, you should be able to check this out in your BIOS. One of the F-keys should take you to the BIOS on bootup.

---

