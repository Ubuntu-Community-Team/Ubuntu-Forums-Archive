---
title: "RAID 0 Build"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by tjvanwyk on 2007-04-04
First post here, *Buntu user for about 4 months. I have middling tech skills, so please explain things slowly. :)

Kind of sort of complex, at least for me, but I'll try to explain as simply as possible...

In the process of building my first computer, and I'm considering a three hard-drive setup, but I want to see how difficult what I want to do will be before totally nailing down my components (catch-22 I guess).

The first disk would be a Western Digital Raptor WD740ADFD 74GB 10,000 RPM, or something similar.  I'd partition this disk for a dual-boot - Ubuntu or maybe Fedora Core, and XP.

The others would be dual Seagate 320GB Barracudas (or something similar, again) in a RAID 0 array, but the array would be strictly for data storage.  In other words, I'd boot my OSs from the Raptor and do my mass storage - including game installation, housing my music library, etc - on the 'Cuda array.

The only other component I think I've nailed down is the Intel Core 2 Duo E6600 2.4gHz as my processor.

So, a few questions: would it be better to format the storage array as NTFS or ext3?

If I go with this build, what do I need to do software-side to be able to write and read to the array from both Linux and Windows?  Is it just as simple as getting a RAID controller, and after that as far as my operating systems will be concerned it will look like one giant 640GB volume?

---

### Post by hush on 2007-04-04
I may be wrong, but I think the RAID array storage HDD's would need to be FAT32 inorder for WinXP and Linux to both be able to read from them. Also, if it's RAID 0 - it would be a 320GB striped array. Both 320GB HDD's split the work in half, speeding up your system, though it can be unstable. If you lose one HDD, you pretty much lose all of the information on both.

---

### Post by freebird54 on 2007-04-04
I am told that ntfs-3g is pretty good now - so that is one way to access from both systems.  Also - there is an explorer-ext3 for windows.  I find that both work both ways - so that should not be an issue - except for the 'journaling' of ext3 gives it a slight edge!

No experience with RAID setups - so I can't help with that.  Rest of the system sounds great though!  ;)

---

