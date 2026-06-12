---
title: "Grub question/help"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-03-27
If grub detects 

Primary master as hd0
Primary slave as hd1

Shouldnt Secondary master be hd2?

Reason i ask i im trying to boot  an OS on my Secondary master but grub keeps saying the drive does not exist. And i know it exist because it shows up in the bios and i installed an OS on it.

Ideas why grub wont detect my secondary master drive? is hd2 wrong?

---

### Post by cacahootie on 2006-03-27
Not necessarily.  Go into your bios settings and check the boot order.  At this point, I have my bios all bass-acked up so it recognizes hdd as hd0, and then associated tomfoolery with the other drives with no relation to cable order.  What bios reports is determined by the boot order list, not necessarily physical placement.

---

