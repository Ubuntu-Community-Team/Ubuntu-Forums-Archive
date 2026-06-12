---
title: "Ubuntu Dual Boot Partitions?"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by LorB on 2005-07-06
I am very new to Linux and I am even new to Mac. Well I am about to install Ubuntu onto my Mac Mini which is a PowerPC G4 and I am wanting to Dual Boot with Mac OS X Panther. In order for me to do this how many partitions will Ubuntu need and how big should they be? My Mac Mini has a Capacity of about 40 GB, 256 MB of memory, CPU Speed of 1.25 GHz, and Bus Speed of 1.67 GHz. Thanks for any help I can get.

---

### Post by varunus on 2005-07-06
Ubuntu only <i>needs</i> one partition; that said, it is strongly recommended that you at least have 2 (usually 3).

Their configuration should be:

swap - one swap partition, usually equal to the amount of RAM in the computer.  (more doesn't hurt; since you have 256 MB, i'd reccommend that)

/ - the main partition, all your software gets installed here.  With that HD, I'd recommend 5 GB, depending on how much software you plan to install.  If you're willing to devote more space/plan on having multiple desktop environments in linux or many many different programs, go with 10, even.  (You can go as low as 2 GB, but you won't be able to install much.)

/home - the place where all your files get stored.  The size depends completely on how many files you plan to save in linux.

You can also use two partitions; just have a swap and a / partition.  (Your home files will then be on the same partition, and this can make upgrades a bit more painful.)  Having /home on a separate partition can help if you screw up and need to reinstall, as your files will stay on their separate partition.

I am currently using Ubuntu on a computer with just a 4 GB / partition and no separate /home, though.  Ubuntu doesn't really need that much space, but its good to have some wiggle room.

---

