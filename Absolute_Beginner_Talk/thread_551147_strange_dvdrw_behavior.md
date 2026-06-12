---
title: "strange dvdrw behavior"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by mc4man on 2007-09-14
on 1of my setups with 2 dvd-rw drives I've noticed that dvd movies (commercial pressed) won't mount as dvd-video when inserted in cdrom0. They always show up as dvd-rom (no label) ie. they're seen as blank media. If I browse the folder it brings up cd/dvd creator. The other drive (cdrom1) works fine. To confuse this more I have another setup w/ 1 dvd-rw and 1 cdr-rw and the same thing happens - when i insert a dvd movie in the dvd-rw drive it shows up as blank media.
On both setups a burned dvdr will mount correctly as dvd-video at /media/cdrom0
whats strange is that in both cases if I insert a cd, let it mount, eject - then the drive (on bothsetups) will recognize and mount a dvd at /media/cdrom0 and will continue to do so properly till i reboot - then the above behavior starts again  :confused:
both setups are feisty 7.04

---

### Post by mc4man on 2007-09-16
gonna bump this once maybe someone with 2 dvdrw drives can ck.
log showing 1st. an attempt to mount dvd, ejecting
then inserting cd, ejecting
then reinserting dvd  

```
Sep 15 17:55:59 doug-desktop kernel: [ 1119.466647] cdrom: This disc doesn't have any tracks I recognize!
Sep 15 17:55:59 doug-desktop NetworkManager: <debug info>^I[1189893359.924768] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_empty_dvd_rom'). 
Sep 15 17:58:52 doug-desktop NetworkManager: <debug info>^I[1189893532.591380] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_empty_dvd_rom'). 
Sep 15 17:59:26 doug-desktop NetworkManager: <debug info>^I[1189893566.847045] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_368906240'). 
Sep 15 17:59:51 doug-desktop NetworkManager: <debug info>^I[1189893591.290584] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_368906240'). 
Sep 15 18:00:26 doug-desktop NetworkManager: <debug info>^I[1189893626.366787] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_label_Ivans_Childhood'). 
```

---

### Post by bone2006 on 2007-09-18
Have you been able to play any dvd movie from it that's commercial?  Out of the box ubuntu can't play DVD movies.  There's a few ways of getting it, but I saw this script recently that can get you dvd, codecds, java, flash..etc

[http://tinyurl.com/398njw](http://tinyurl.com/398njw)

---

### Post by mc4man on 2007-09-18
I can play dvd's fine it's only after a fresh boot that 1 dvdrw drive will see commercial dvds as blank dvd'. After inserting a cd into that drive, then ejecting it will then recognize commercial dvds (and play) till I reboot

---

