---
title: "[live cd] cannot copy/paste between 2 drives"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Channy on 2007-06-08
Hi i have three drives (one IDE and two SATA). I would like to use ubuntu live cd to backup some files from two of the drives to the third drive.

I placed the cd in the computer, and ubuntu live cd booted up fine. But i cannot copy/paste or make a new folder on any of the drives.

Is it something to do with me not being the admin on ubuntu?

Oh! and also the IDE, and one of the  SATA drives have XP installed. (they're the one i want files to be backed up from, as im wishing to format them.)

Any ideas?

---

### Post by proalan on 2007-06-08
are all 3 drives formatted as ntfs? windows xp should be by default

linux isn't able to manipulate files on ntfs format by default, you need to install ntfstools but that can only be done from a linux installation not a liveCD.

however if you can spare a harddrive reformat it to FAT32, ubuntu supports read and write access for that by default.

---

