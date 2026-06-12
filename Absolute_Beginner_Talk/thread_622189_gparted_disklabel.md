---
title: "gparted disklabel"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by noezoom on 2007-11-24
i had a dual boot with windows xp and ubuntu 7.04.  i wanted to reallocate a partition that was going unused, and in the process created an msdos disklabel for my entire hard drive.  now when i boot, grub gives me an error 22.

is my hard drive blank now?

i was thinking about getting a hard drive enclosure to connect it to my laptop via usb and backup whatever i can find on there, but i don't want to spend the 30$ on that if it's just going to be a waste of time.

i don't have a windows xp cd to boot into recovery mode.  i got a dell, and they just don't do that.

anyone know what i can do to save my lost data?

---

### Post by ravenizer on 2007-11-24
There is a possibility that your HD is blank. Technically speaking, when two primary partitions containing OS are combined, there is a conflict and the disk becomes unbootable.:( You may try this alternative though. 

Get Parted Magic, a live CD linux disk partitioner. Check to see if you can reformat the MS Dos partition to something lse like NTFS.Then try rebooting again.:confused:

Thats the best i can think of from what you have provided. Hope it works.:)

---

### Post by noezoom on 2007-11-24
i could try that.  most of the stuff i want to save was on the ntfs partition.  do you think it would let me get to the ntfs stuff after that and just ignore the ext3 (or whatever) partitions?

---

### Post by mc4man on 2007-11-24
There are ways to get to the recovery console without an xp disk, though at this point it may of no value. If needed start here
[http://commandwindows.com/recovery.htm](http://commandwindows.com/recovery.htm)
In the future keep in mind that with gparted you can't/don't give partitions names (volume labels) like you can in windows disk management

---

### Post by noezoom on 2007-11-25
well, i loaded parted magic and i ran gparted from it and the disk was a big unallocated gray box.  i thought ravenizer had suggested relabeling the drive as ntfs, not formatting it as ntfs.  that sounds like it will definitely delete everything i had.

then i went to the windows xp recovery console from mc4man's link and that couldn't tell that i had a windows installation on the disk.  so i guess it can't recover.

before i start reformatting it or attempting to use the hidden dell recovery partition, does any one think there's a chance i could plug it into another computer as a secondary hard drive and maybe get to the data on there?

it was such a quick operation to relabel the disk, i'm having a hard time believing that my stuff isn't still in there.

---

### Post by mc4man on 2007-11-27
Do a search for hdd data recovery tools, you may be able to salvage some things

---

### Post by tobiasz.cudnik on 2008-05-08
FUT [http://ubuntuforums.org/showthread.php?p=4915485#post4915485](http://ubuntuforums.org/showthread.php?p=4915485#post4915485)

---

