---
title: "[SOLVED] Reinstalling Vista"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by le-meas on 2008-03-06
Hi.

**I have Gutsy Gibbon but I want to reinstall Vista on another partition.**

So, I repartitioned the drive in the ubuntu installation. 160gb[100%] was dedicated to ubuntu so when I repartitioned it, I dedicated 40gb to ubuntu and the rest formatted as a fat32 partition with no mounting point. I wanted to leave this for vista.
All that went well and I now have ubuntu working fine.

I then tried to install vista. I clicked format to make the partition NTFS. No problem occured...at least that is what I thought...It wont let me install vista, it keeps trying to say that I dont fit the requirements...I read something on the internet saying that a ntfsfix file may have to be used...Is this true? Also, how would I go about this?

Cheers,

***Le-Meas***

**additional:**
The error given is: "Windows is unable to find a system volume that meets its criteria for installation."

---

### Post by jimv on 2008-03-06
Go back into Ubuntu and delete the FAT32 partition, so you just have 120 gigs of unpartitioned space on your HD.  Then, when you install Vista, let Vista create the partition in that free space.

---

### Post by le-meas on 2008-03-06
> **jimv said:**
> Go back into Ubuntu and delete the FAT32 partition, so you just have 120 gigs of unpartitioned space on your HD.  Then, when you install Vista, let Vista create the partition in that free space.

Sorry for been a newb but how do I do that?

---

### Post by neurostu on 2008-03-06
there is program called "Gnome Partion Editor" (G Part Ed) that you can use. It should be under application system tools, I think.... Or you can download the GParted liveCD and use that to delete the partition.

---

### Post by neurostu on 2008-03-06
Actually if you want to use the entire HDD you will have to use the GParted LiveCD  as ubuntu won't let you work on a mounted drive (the OS drive needs to remain mounted, ubuntu won't let you unmount its HDD)

---

### Post by MasterJS on 2008-03-06
actually it would be easier to just boot into the Live CD, open up a terminal, and type GParted. Then you right click the FAT32 partition and delete it.

---

### Post by billgoldberg on 2008-03-06
I had the same problem when I wanted to install vista a few months back (this pc came with vista, so it's capable).

I formatted the partition a few time with other programs every time, it didn't work.

It was only to play a game, I got it running in wine, so I never solved it.

---

### Post by le-meas on 2008-03-07
Worked perfect. Able to use vista again and enjoy multimedia...

---

