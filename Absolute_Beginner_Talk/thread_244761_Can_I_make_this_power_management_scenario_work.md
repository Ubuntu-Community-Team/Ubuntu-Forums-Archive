---
title: "Can I make this power management scenario work?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by nondystam on 2006-08-26
I'm running Ubuntu Server on an older S478 P4 processor - the motherboard supports both ACPI and APM (Asus P4P800-E).

In regards to power management, I would like to set it up so that after X minutes of inactivity, the system goes into some kind of power saving mode (standby or suspend to disk/ram - doesn't particularly matter) and can be woken up again via Wake on Lan or pressing the power button. ethtool reports that the integrated Marvell Gigabit NIC supports WOL via magic packets, so there should be no issues from that perspective. I'm not going to be accessing the the server all that regularly, but when I do, i'd rather it be in a "half on" state than completely powered off.

Using Windows, making this scenario work isn't too difficult. I would like to do the same with Ubuntu Server, but within the standard text (console) mode, and not within GNOME/KDE. From doing a bit of hunting around, i've found sleepd might do what I'm after, but it appears to be unreliable. I can't see any options within swsuspend2 that will help me do what I want.

So can it be done? Or do I have to bite the bullet and use something like GNOME and the gnome-power-manager?

Cheers

---

