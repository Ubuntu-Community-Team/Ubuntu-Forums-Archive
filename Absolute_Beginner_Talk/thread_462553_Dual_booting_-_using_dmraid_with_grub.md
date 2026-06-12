---
title: "Dual booting - using dmraid with grub"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by kevpatts on 2007-06-02
Hey,

I need to configure my system to dual boot with XP (for game playing only). My Ubuntu is on an IDE drive but my XP is on a RAID 0 array. Using dmraid and ntfs-3g I can mount the array (it's /dev/mapper/nvidia_ebgeeceg) but I can't seem to boot to it through an option in grub. I've tried adding ```
(hd3) /dev/mapper/nvidia_ebgeeceg
``` into devices.map and using it in menu.list but I get an error. I've also tried using just (hd1,0) in menu.list (which points to /dev/sda) but I also get an error. Is there any way I can configure this?

Kevpatts

---

### Post by arkham on 2007-06-06
I managed to get grub to work using the info here - though I was not trying to dual boot windows.  Since that is specifically what the tutorial i written for, hopefully it will help.

[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

---

