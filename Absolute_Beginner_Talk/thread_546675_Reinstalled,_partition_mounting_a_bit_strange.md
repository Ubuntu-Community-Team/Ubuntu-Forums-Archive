---
title: "Reinstalled, partition mounting a bit strange"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Ace02 on 2007-09-09
I just recently reinstalled Ubuntu, within the past hour or so. I've had it for just a couple of days, I messed some things up, so I just wanted to reinstall it... Anyway, in the partition part of the installation, I manually ticked in format on my old Ubuntu partition, and set it as the root partition. Just a few hours ago, my Windows partition used to always show up as "Volume 220GB," and I would mount it to get access, and it would show up on my desktop as "disk." Now it shows up on the desktop as "sda1," without me ever mounting it and I can't unmount it... I get this error:

> 
[SIZE="4"]Cannot unmount volume[/SIZE]

Cannot unmount the volume.

_D_etails
unmount: /media/sda1 mount disagrees with the fstab





Is this a problem? Does anyone have any idea why this happened?

---

### Post by mikeyphi on 2007-09-09
This is NOT a problem! Your windows partition is permanently mounted because there is an appropriate entry in your fstab. If you don't want it this way - you will need to edit your fstab

---

