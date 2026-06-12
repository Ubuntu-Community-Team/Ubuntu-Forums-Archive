---
title: "Boot problem after install on AMS 64bit 3500"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by etxkesa on 2007-08-03
I have been looking for any hints on this problem but haven't found anything. 
I downloaded and burned the AMD 64bit release of 7.04. It ran perfectly as a live version from the CD, but when I installed it to my IDE drive (40GB, I have 2 SATA drives one with XP and the other user data) and rebooted I got an error saying that it couldn't handle the clocking of the CPU. I'm running on a pretty vanilla Gigabyte mobo with no over clocking at all. Any ideas what the problem might be?

I checked the CD and it came up OK.

---

### Post by Midahed on 2007-08-03
You have three drives -is that right - One IDE and two SATA?  Which drive does your system normally boot from?  Presumably it's the SATA that has your XP installation on it?

How is your boot process set-up - are you using BIOS settings to tell your system to boot from the IDE drive when you try to run Ubuntu or are you using a bootloader?

Have your tried using the live CD to tell the system to boot from the first hard disk (assuming you can configure your BIOS to make the IDE drive the first boot device.  Alternatively I think the SystemRescueCD (Googling will return plenty of links to it) allows you to specify which drive you boot from.

That's a very odd error to be getting, so I'm not sure if this will help....

[EDIT]  By the way, what is the exact wording of the error message and when in the boot process do you see it?

Mike

---

### Post by Midahed on 2007-08-03
One other thought....

Features like "Cool 'n Quiet" and power saving stuff vary the CPU clock speed to reduce power consumption when the CPU is less active.  On my system I found I had problems with the speed of 'system time' in a guest O/S running under VMware Server.  This was all down to the way in which VMware was interpreting what was happening to the system clock.  Obviously your problem is nothing like that, but if we take the error you're getting at face value, it may be worth turning off "Cool 'n Quiet" and any power-saving features that your BIOS may support.  It may have nothing to do with the problem (in which case the error message is very misleading), but it won't do any harm and it might tell us something about what's going on.

Mike

---

