---
title: "Convert NTFS to FAT32 w/o loss?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by puterboy on 2006-06-13
So i googled this, and it said to use partitionmagic to convert from ntfs to fat32, so that my newly installed linux sys can read/write with no problems. unfortunately, pm wants to convert to a logical partition first, and then it says that it's a windows partition (i have a backup copy of xp on there). so can i convert using ubuntu so that it does not check for it to be a windows partition without losing the 300 gigs of data on the drive?

---

### Post by u.b.u.n.t.u on 2006-06-13
I personally wouldn't risk 300GB of data like that. Maybe if I knew it was fully backed up and tested.

I would opt for an extra HDD with the data secure in case something goes wrong. Better safe than sorry.

---

### Post by jrd on 2006-06-13
Do you have enough free space to make a new partition (fat32) then just copy your ntfs partition to it?

---

### Post by puterboy on 2006-06-14
well, here's kinda an update. i was able to scrounge enough space on other drives to backup all my files. here's the catcher: windows identifies my drive with my ext3 partition as bad (the whole drive). therefore, my other hard drive can't be changed because windows doesn't want me to remove both active drives. i can still boot off the first drive and stuff, just not view it's different partitions. if i try it via ubuntu, i run into the problem of not being able to work with an NTFS drive. anyone know of anything for Partition Magic that'll let it see my ext3 and swap partitions? or maybe a program? i've only heard of PM working without losing all the data

---

### Post by jimrz on 2006-06-14
[QUOTE=puterboy]well, here's kinda an update. i was able to scrounge enough space on other drives to backup all my files. here's the catcher: windows identifies my drive with my ext3 partition as bad (the whole drive). therefore, my other hard drive can't be changed because windows doesn't want me to remove both active drives. i can still boot off the first drive and stuff, just not view it's different partitions. if i try it via ubuntu, i run into the problem of not being able to work with an NTFS drive. anyone know of anything for Partition Magic that'll let it see my ext3 and swap partitions? or maybe a program? i've only heard of PM working without losing all the data[/QUOTE]

   i have PM8 and am able to see all of my partitions ext3/linux swap/fat32/ntfs using it on win xp.

   i have not tried to do what you are wanting using this combination. however, a couple or so years ago i did use PM6 (i think, thrashed the cd and never made a backup copy...duh) running on win2k to convert ntfs (secondary hd, not the win partition on the primary) to fat32 without any problem and had no data loss. the only thing you must be sure of (other than having your data backed up) is that the partition is no more than about 40-45% full. since PM needs plenty of room to move stuff around during the conversion.

---

### Post by CarpKing on 2006-06-14
Not sure if this will help, but you can get drivers to allow Windows to read and write to your ext3 partition at [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html).  Might perhaps help with the problem of Windows not liking your drive.

---

### Post by puterboy on 2006-06-14
Well, i ended up just deleting most of the media, and transfering the rest to a new drive, then reformating into FAT32. Those drivers don't work for me, AMD64....

Anyway, everything's copied back on, but one little problem. I can't change the permissions for the "my music" and "my pictures" folders i transferred straight from windows. i could go back into windows and change it, but how could i do it via terminal?

---

