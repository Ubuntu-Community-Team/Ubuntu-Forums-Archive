---
title: "Secondary Hard Drive Frezzes Boot"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by branflakes613 on 2008-03-05
I am new to Ubuntu. I originally had two hard drives with windows XP on one of them but because of some errors i decided to try Ubuntu. When i tried to install Ubuntu off of the livecd i couldn't because when i would select start or install the splash screen would pop up then freeze and after waiting for a while a page that says"BusyBox v1.1.3 {Debian...(initramfs)" would appear. So just for the heck of it i took out my secondary hard drive and magically the install works. After having Ubuntu on only one hdd i decided hey why not try to put my other one back on. I hooked it up and everything worked smooth until the splash thing again. the orange bar would only move a little then the computer freezes and eventually kicks out of it back into the busybox thing. The secondary hard drive is a Seagate barracuda 250gb both are ata. any help would be appreciated.

---

### Post by stalkingwolf on 2008-03-05
Check the jumper.  Make sure it is set to either slave or cable select.  There should be a guide
on the drive for jumper settings.  If not you can find them on seagates website.

---

### Post by branflakes613 on 2008-03-05
Thanks for the advice. It was already set on secondary so i tried cable select and i got the same results.

---

### Post by stalkingwolf on 2008-03-06
Busybox is part of the repair/rescue app.  It may not be freezing but trying to repair the drive.
This can at times take a long time especially on large drives.

---

