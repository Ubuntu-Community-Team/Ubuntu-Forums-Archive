---
title: "Partition format that Mac OS X can mount"
date: 2009-06-29
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-06-29
What I would really like to do is partition an external disk and create a partition in the right format, so that it can be mounted by Mac OS X and also shared by other Mac OS X systems on a LAN.

Could someone please advise the partition format I should use?

---

### Post by PerilousPete on 2009-06-29
OS X can mount HFS+, FAT32 and NTFS. NTFS is read only, but the others can be written to. Choose FAT32 or NTFS if you want Windows computers to be able to access as well.

---

### Post by sulobanks on 2009-06-30
You can read and write hfs+ from linux and mac.  You just need to turn off journaling.  The main issue is syncing users.  Your users in linux and os x need to have the same uid's.  I've got the same uid for my user in linux and os x and I've got a hfs+ partition with journaling off.  It works perfectly regardless which system I boot into.  I've also done this with a few external drives I use for backup.  Haven't had any permission problems.

I'm not sure what kind of network sharing you're after, though.  Do you want to share the drive from an os x system?  Or are you wanting to share it over the network from your linux system?

---

### Post by MikeTheC on 2009-07-01
If you install MacFUSE and the NTFS-3G module, you can read and write NTFS-formatted partitions.

Your best bests for partition options are the modern Linux ones, HFS+, or NTFS, because all of them support >2.1GB file sizes. HFS, FAT32 and some others do *not*.

---

