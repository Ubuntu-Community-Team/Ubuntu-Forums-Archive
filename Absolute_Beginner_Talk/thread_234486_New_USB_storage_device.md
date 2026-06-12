---
title: "New USB storage device"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by frrobert on 2006-08-11
I just added a usb storage device to a computer that didn't have it when I installed ubuntu.  If I add it then reboot it does not see it.  But if I boot with the live cd the device is seen.

I'm thinking the reason it is not seen is that usb storage device and the scsi device module isn't loaded.  The problem is both those modules don't seem to been copied to the HD during istall.  So the question is how can I load those modules?

---

### Post by xpod on 2006-08-11
Dont you need to make a mount point for it then mount it like any other device....

Or is it different for usb?

---

### Post by frrobert on 2006-08-11
That is true but i'm not getting to that point.  The device itself isn't being seen because the drivers are being loaded.

---

### Post by xpod on 2006-08-11
Sorry im not sure i know what you mean..It`s not showing up if you" sudo fdisk -l"...Because the drivers ARE being loaded.

That is where your looking i take it?....have you plugged it in and rebooted and its not there OR are you just pluggung it in and looking???

Sometimes my various usb devices get wonky and it`s better to plug it in and reboot.....It should show up somewhere though eh

edit:sorry you have rebooted....might need some special driver.

Sorry im no help

---

