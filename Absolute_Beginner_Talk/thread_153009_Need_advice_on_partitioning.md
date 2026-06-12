---
title: "Need advice on partitioning"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Gump Stump on 2006-03-31
I have a new computer with a single 300 GB hard drive, with no partitions yet (Windows XP already installed). I want to partition it to prepare it for installing Ubuntu, so I'd like some advice on this setup:


30 GB - NTFS - Primary partition - Windows OS
20 GB - EXT3 - Primary partition - Ubuntu OS
30 GB - FAT32 - Logical partition - Section for files etc. to share between XP and Ubuntu
216 GB - NTFS - Logical partition - Section for games, videos, etc. for XP use
2 GB - EXT3 - Logical partition - Ubuntu swap
2 GB - NTFS - Logical partition - Windows paging file


Is this a good way to partition things? Will I have to repartition when I install Ubuntu, or will it recognize what I've set up for it?

Thanks in advance...

---

### Post by Perfect Storm on 2006-03-31
Maybe be a good idea if you have a seperate /boot in the start.

---

### Post by meborc on 2006-03-31
if you make the partitions under xp, ubuntu will recognize them.. so dont worry... you just need to install ubuntu in the right partition...

only one Q: why are you making a small partition for ubuntu and xp to share and a big partition for xp games and videos...?

i would add them together and make a 246 GB FAT32 partition... you can install games there (from win) and all your videos... so you can access the videos/music from ubuntu as well without copying them all the time to the small partition... just my 2 cents... ;)

---

### Post by Praetorian on 2006-03-31
[QUOTE=Gump Stump]
2 GB - EXT3 - Logical partition - Ubuntu swap
2 GB - NTFS - Logical partition - Windows paging file
[/QUOTE]

Why do you need so much swap space?
Don't know how much ram you have but I think that 512 MB swap is enough

---

### Post by Perfect Storm on 2006-03-31
It really depend on how much ram he have. I agree, it seems a bit overkill here, but again we don't know how and what he want to use his computer as.

---

### Post by Gump Stump on 2006-03-31
[QUOTE=meborc]if you make the partitions under xp, ubuntu will recognize them.. so dont worry... you just need to install ubuntu in the right partition...

only one Q: why are you making a small partition for ubuntu and xp to share and a big partition for xp games and videos...?

i would add them together and make a 246 GB FAT32 partition... you can install games there (from win) and all your videos... so you can access the videos/music from ubuntu as well without copying them all the time to the small partition... just my 2 cents... ;)[/QUOTE]


Thanks for the reply. As far as I know I can't make a FAT32 partition larger than 32 GB, so that's why I wasn't going to make the >200 GB partition a FAT32 volume. Can I do that?

---

### Post by Gump Stump on 2006-03-31
[QUOTE=Praetorian]Why do you need so much swap space?
Don't know how much ram you have but I think that 512 MB swap is enough[/QUOTE]

Thanks for the reply. I have 1 GB of RAM, and it was my understanding that you should have about 2x your RAM capacity in drive space for the swap. Can I combine the Windows paging file and the Ubuntu swap in a single 2 GB FAT32 partition? Only one OS will need it at a time, right?

---

### Post by infoseeker on 2006-03-31
2 x RAM...up to 512MB...if I recall.
Me myself have never seen more than 20 MB swap file use....and I have 512 MB RAM.

---

