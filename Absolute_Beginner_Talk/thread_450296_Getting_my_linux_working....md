---
title: "Getting my linux working..."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by RogerRogerson on 2007-05-21
Here's my system setup
Core 2 duo
X1950pro
2gb ram
160gb ide, 80gb sata (Ubuntu has no problem detecting this, as I have it plugged into the ICH8 chip)
gigabte 965p-ds3 (It appears ubuntu detects everything I need fine, sound works fine and fan control is done through the BIOS or the stock cpu fan is really quiet)
d-link dwl-g510 rev c (rt61 chip) (To connect to this in windows I just have to check the box saying allow me to connect even though theres no ieee authentication)
billion router - network has no ieee authentication or wep/wap keys enabled

What I've done is reformatted my 160gb hard drive, it has windows isntalled on one partition, which is 25gb, then I believe a 2.5gb linux partition (for feisty fawn) and a 500mb swap partition, the rest of the ahrd drive is a fat 32 partition.

The 80gb drive is in NTFS and I'm not too keen on changing it.

Being the total n00b I am I have 2 problems.

I cannot choose to boot into linux, and whilst feisty fawn does detect my router, I can't seem to connect to it (I've only done this when I've installed it to my RAM).

I have ndis wrapper and the rt61 drivers on my fat32 partition, however I have no idea how to get it working, probably because I haven't completely scrutinised the help files. If someone could give me a step by step walkthrough on how to boot into linux and then get my wireless card working so I can get access to the internet that would be great.

---

### Post by drowner on 2007-05-21
Need more info.


What did you install first... windows or ubuntu? WinXP or vista?

do you get a GRUB screen at all? Or does it just boot windows?

---

### Post by RogerRogerson on 2007-05-21
I installed xp home first, never got/get a grub screen, just loads xp home straight away. Could this be because I downloaded the amd 64 version (I assumed my core duo-2 was a 64bit processor, the live cd works fine)?

---

