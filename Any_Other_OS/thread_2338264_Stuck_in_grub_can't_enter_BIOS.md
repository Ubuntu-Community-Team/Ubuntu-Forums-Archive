---
title: "Stuck in grub: can't enter BIOS"
date: 2016-09-26
forum: Any Other OS
---

### Post by kguardado on 2016-09-26
I wanted to delete the ubuntu partition that I had as dual boot on my windows 10 computer. So I went ahead and deleted the linux partitions and created a windows 10 recovery drive to boot from. Unfortunately, I forgot about grub and now I can't seem to find a way to boot into BIOS so I can boot from the recovery drive. 

The whole reason I went through the removal is because I left my computer unattended while I was updating and a kid got to it. I had no idea what the kid had done to it, but it was clear it had been corrupted. So I thought I'll just uninstall and reinstall. So while I deleted the linux partitions, the partition is still there (I didn't extend my others). I made an iso bootable drive with linux on it. If easier to get linux on it first from grub I can do that.

But right now I'm still stuck in grub and can't figure out how to boot from a drive. :/

---

### Post by oldfred on 2016-09-26
UEFI or BIOS?

If newer system, it may have fast boot in UEFI which is different than the fast start up issues with Windows.

If fast boot is on, then you do not have time to press a key to change any system settings. Fast boot assumes everything is the same as previous boot and immediately starts system. 

You may be able to cold boot, full power down, if laptop remove battery and then hold power switch for 10 sec or so to drain all power. A few have had to open system and remove coin battery on motherboar or jumper pins on motherboard to totally reset system. But then you have to change all BIOS/UEFI settings again as it restores to defaults.

---

