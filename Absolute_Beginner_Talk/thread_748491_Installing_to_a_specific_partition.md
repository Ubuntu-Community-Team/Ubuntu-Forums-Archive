---
title: "Installing to a specific partition"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by hapveg on 2008-04-07
Yesterday my raid 0 died (again), it was just my WinXP gaming setup, my important stuff is on a separate Ubuntu drive. I'm getting a new hard drive delivered tomorrow (1TB Western Digital Green Power).

Previously I've always had WinXP and Ubuntu on separate hard drives, but since the new drive is huge I'd like to put them both on the same drive.

The Western Digital Green Power is eco-friendly, low power, but also a bit slow. The start of the drive gets about 80mb/s, the end only gets 50mb/s.

I really don't want Ubuntu to be installed at the end of the drive, and from what I can see, that's where the normal Ubuntu installer puts it.

When installing WinXP I am planning on creating the following partitions:

Partition 1: 10gb C: WinXP system partition
Partition 2: 10gb Ubuntu partition (or 9+1gb for swap).
Partition 3: 10gb D: Windows tools (firefox / open office / etc)
Partition 4: 300gb E: Windows games
Partition 5: ~670gb F: Generic storage for both Ubuntu / WinXP

With the above setup the important sections (booting / tools) will be at the fastest part of the drive, while the generic storage section will be at the slowest part. I don't really care about the order of the first 3 partitions, just so long as neither WinXP or Ubuntu is at the slow end of the drive.

How do I install Ubuntu on partition 2? When setting up the partition in the WinXP installer should I split partition 2 into a 9GB and a 1GB section (for swap), or just leave it at 10gb?

Any help appreciated.

---

### Post by Duck2006 on 2008-04-07
Partition the drive first with gparted or parted magic. Gparted can be used from the ubuntu live cd.
Install win then install ubuntu, with the installer on the ubu ntu live cd use the manual install and tell it where you want to install ubuntu and it will install for you.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Existentialist on 2008-04-07
I would install xp first by creating the 10gb ntfs partition.  After that, boot up the live cd for the ububntu installer and create the rest of the partitions.  Since you can only have 4 primary partitions, you will need to use logical partitions for 3 of your partitions.  You will have to separate your ububntu and swap partitions.  When installing from the live cd, you can format all the windows partitions ntfs so that windows sees them, and then set up your linux partitions as ext3 and swap and locate them wherever you would like on the drive.

---

### Post by hapveg on 2008-04-07
Thank you both greatly.

I'm going to try Duck2006's suggestion, my nice monitor is away for repairs, and I'm using a very old Samtron 15" CRT, which has known problems with Ubuntu (can't boot a LiveCD with it, even in safe mode), but my already installed Ubuntu half works (can display gnome at 800*600, can't display anything until the gnome loads).

gParted installed fine on this system, and it looks like it'll be perfect.

I'll use gParted to create:
Primary: 10gb - WinXP drive C
Primary:  9gb - Ubuntu Ext3
Primary:  1gb - Swap
Extended: ~980gb
--- Logical 10gb - Windows tools
--- Logical 300gb - Windows games
--- Logical 670gb - Misc

Then install WinXP as normal, and when my monitor get repaired install Ubuntu.

Thanks again.

---

