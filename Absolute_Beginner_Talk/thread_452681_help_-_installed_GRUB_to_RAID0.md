---
title: "help - installed GRUB to RAID0"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by beav on 2007-05-23
I "destroyed" my RAID-0 by installing grub to the wrong device.  I want to recover the data if possible.

Setup:
Abit TH7-II (i850) RAID w/ integrated Highpoint 3.7 controller
IDE0 - optical drive
IDE1 master - WinXP
IDE1 slave - Ubuntu Feisty
IDE2, IDE3 - 2 x WD800JB, NTFS in RAID-0 for media

Highpoint tells me one of the drives in my array has failed, with options to delete the array or ignore.  WinXP sees one of the drives, but can't access it.  Feisty sees a 160GB partition it can't mount, and reports wildly different CHS geometry for the two identical drives.

The demo of GetDataBack sees my directory structure, but can't extract any files.  Raid Reconstructor can't suggest any significant parameters.

What should I do?

---

### Post by dstew on 2007-05-25
If your Feisty is running, you can try to recover your RAID from there. The dmraid program is what Linux uses to manage RAIDs.  [Here]("http://www.die.net/doc/linux/man/man8/dmraid.8.html") is the man page. You can install dmraid using Synaptic. You need to have the Universe repository enabled (in Synaptic --> Settings).

There is also this [How-To]("https://help.ubuntu.com/community/FakeRaidHowto") that discusses installing Linux on a RAID. I know that is not your issue, but I think there are some links there that might point you in some helpful directions.

---

