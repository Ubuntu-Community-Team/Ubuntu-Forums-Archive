---
title: "HD no longer recognized by Mac OS after Feisty upgrade"
date: 2007-06-24
forum: Apple PPC Users
---

### Post by crimson on 2007-06-24
My problem: I recently did an install of Feisty Fawn to a G4 Cube that was previously running Ubuntu (Dapper and then Edgy), and also set up to boot into Mac OS 9.2 for a few old programs I still want to use on occasion. After the installation, I can no longer boot into OS 9, nor will the OS 9 installer CD see the Mac HFS+ partition, although Linux mounts it fine (and everything is still there).

I wasn't able to get either the Ubuntu upgrader or apt dist-upgrade to get the right files, so I thought I would just do a full installation. I figured my system needed a little pruning anyway. I had a spare partition already, so I didn't make any changes to the partition layout, although the "expert" installation on the alternate install disc did make me go through a partition editing step. I didn't expect any problems, though, since I wasn't changing anything.

My guess is that one of the Mac-specific partition blocks has somehow been munged, but I have no idea how to go about investigating this or fixing it.

So my questions are: Has anyone encountered this, and maybe have an idea what has happened? And can anyone suggest some tools (Linux or Mac) that might be used to recover the damaged partitioning info (if that's what it is).

Thanks!

---

### Post by rectagonal on 2007-06-24
Do you have an OS X boot cd ? If you can "see" the hard drive from the OS X installer disk. It sounds like you have damaged what the OS X Disk Utility refers to as the "Mac OS 9 Drivers" for that partition. 

I have no experience with fixing this non-destructively or much experience with OS 9 .. but ..

According to apple's documentation Drive Setup on the Mac OS 9 CD can restore these drivers non-destructively to allow OS 9 to see that drive again. Info here - [http://docs.info.apple.com/article.html?artnum=106849](http://docs.info.apple.com/article.html?artnum=106849)

---

### Post by crimson on 2007-06-24
Thanks for the idea, rectagonal, but unfortunately, Drive Setup on OS 9 says the drive is "not initialized" and the "Update Drivers" menu option is dimmed.

The OS X 10.2 boot CD, however, **does** see the HFS partition! And First Aid verifies that the contents are okay. I guess I'll start investigating what parts of the old Mac hard drive formatting are no longer used by OS X. My suspicion lies with the Apple_partition_map on hda1.I don't know of any tools to look at or work on it, though.

---

