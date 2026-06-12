---
title: "Query about intended partitioning"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by flarkit on 2006-04-03
Hi

I realise that partitions are a regular topic, but I'd like to hear whether my notions are sound, or not.

I currently have a 120Gb P-ATA disk, used mostly for XP with 15Gb allocated for Linux fiddling.

I'd like to get 2 80Gb SATA300's which I won't be running in RAID, after hearing of some scary installation troubles. Instead, I'm considering the following scheme:

DISK0 (80Gb)
- 30Gb XP OS
- 30Gb NTFS (apps)
- 14Gb Linux ***data***

DISK1 (80Gb)
- 2Gb NTFS (XP pagefile)
- 512Mb Linux swap
- 10Gb Linux OS
- 62Gb NTFS (games, data)

DISK2 (120gb)
- FAT32 (data)

Mainly, I was wondering whether the first 3 partitions on the second 80Gb are an efficient layout or not?
:-k

---

### Post by waster on 2006-04-03
Partitions are okay, apart from the XP issue, and hence all the NTFS and XP stuff. Why do you have any NTFS? FAT better if you're dual booting, as it requires less messing around. I don't think there is native NTFS R/W support. 512 a bit small for swap. Can you spare 1Gb?

Software RAID not a problem. Installation marginally harder, but worth the effort. If you do this, try to get the RAID partitions in the same places on each of your big disks.

---

### Post by meborc on 2006-04-03
i'll just give you my idea of partitioning... 

it consists of 4 parts:

1) win xp installation on a NTFS partition (not FAT as NTFS has a lot of advantages over FAT when using under win) not particulary big partition... about 20 GB max (who uses win anywayz?)

2) A big, and i mean A BIG FAT32 partition, about 200 GB (or whatever you can spare) where all the xp games and documents and videos and music is saved, so that they could be accessed both by xp and linux (linux can read NTFS but not write on in, not successfully anyway)

3) A Linux install partition... 20 GB

4) A linux swap partition 1 GB

the idea is to have all your documents and videos and music and stuff under one partition... easy to find, easy to mount/umount... and just pure clean partitioning ;) 

now this is a case when 1 HD is used... in your case you must make some modifications... but you get my idea

---

### Post by Fozzie on 2006-04-03
NTFS is important for video editing. NTFS does not have the 4 gigs file size limit that FAT32 is stuck with. An hours worth of captured DV camcorder footage occupies around 12 gigs. I have been keen to move from away from commercial OSs to Linux, but the video apps to match those available to XP/Macs are only now emerging. Cinelerra looks impressive, but needs massive hardware requirements. Kino I have not yet seen, but I believe it is quite basic (correct me if I am wrong). LIVES and Jahshaka look promising, but are in development. So, while I would love to dump Windows, I am stuck with it. WINE is another possibility for running Windows apps in Linux, but again is still in development. Could it cope with the high demands of video? Looks like a dual boot setup is necessary for the time being. Just thinking aloud here. At the moment all my drives/partitions are NTFS which can only be changed by deleting them. I would have to clear a drive and reformat it as FAT32 (for Ubuntu), but leave the others NTFS.

---

### Post by flarkit on 2006-04-04
@waster: I was planning to set aside 2x2Gb partitions for the Win pagefile and for Linux swap, but I saw a mention somewhere that more than 512Mb was actually a bad idea.

The reason for the whole bunch of partitions is as-follows: I thought that there may be some benefits to having the OS on a different disk to the one holding the swap area. There'd also be benefits to having the OS as near to the front of the disk as possible.

With 2x80Gb, I chose to give XP the front of the first disk, with its pagefile sitting at the start of the first disk. Perhaps I could try and convince Linux to use the first 512Mb of the XP disk for its swap space.

Then I thought that it would be good to have the OS on a separate disk to the apps disk. This is where I'll re-plan the layouts a bit. Perhaps something like:

DISK0
- 2Gb Linux swap
- 30Gb XP OS
- 40Gb NTFS (data, mostly docs and install files)

DISK1
- 2Gb NTFS (XP pagefile)
- 10Gb Linux OS
- 62Gb NTFS (apps + games)

DISK2
- FAT32 (shared data)

---

### Post by waster on 2006-04-04
You're correc that having OS on different disk(s) to swap is good. I didn't know abou the FAT32 limit. Can Windows mount a Linux partition? Too much swap is never a problem, within reason.

N.b. linux will automatically stripe (RAID0 style) across available swap partitions.

I'd consider RAID if you are doing huge video edits. If you're throwing around huge files, a big swap would be useful: I'd go 2gb. Hope you've got at least 1Gb RAM.

RAID1 halves your capacity, but read speeds are nearly doubled at the expense of fractionally slower writes. For video editing, you might want a very fast RAID0 area for working, before saving to RAID1 area (or DVD).

Access times can be slightly better at start of disk, but don't get too hung up on it.

Concentrate on sorting out read/write access for NTFS. You clearly need some bigger disks soon anyway, if you're producing 12gb here and there.

Is disk 3 4gb in size? If bigger, then spread your data/os/swap across three disks, using RAID where you can.

---

