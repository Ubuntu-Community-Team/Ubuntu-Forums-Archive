---
title: "Partitioning and mounting dual boot XP/Ubuntu install"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Jdoki on 2007-04-06
Hi all,

I finally decided to try and move away from Windows, and I'm currently on Step 5 of the Ubuntu install from the Live CD... but I'm a bit concerned by what happens next...

I have one hard drive in my laptop, which was originally divided like this:

4GB - Windows rescue partition (FAT32)
The Rest - NTFS partition containing Windows XP MCE

I chose to manually change the partition table at Step 5 of the Ubuntu install, and resize/split the drive as follows.:

4GB - Windows rescue partition
47GB - Windows XP MCE NTFS Primary partition
20GB - Primary partition created as Ext3 for "/"
2GB - Primary partition created as Ext3 for "swap"

I want to keep the Rescue and Windows partitions so I can dual boot Ubuntu or XP as needed.

Was it correct to create the two ext3 partitions as Primary rather than Extended?

Now, the next two screens is where I'm getting really confused.

The next screens asks which partitions I want to use - choosing the 20GB for "/" and 2GB for "swap" is no problem, but why does it show the following as Mount Points for the Windows and Rescue partitions...

/media/sda1 for the 47GB Windows area
/media/sda2 for the 4GB rescue area

Should I blank these lines or leave them as is?

I have moved onto the next step and my concern here is the Warning message:

"This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted"

Obviously my first thought was that if I blanked the /media/sda and partition lines on the previous screen then I would lose the data on these as well.

If anyone can advise me I'd be really grateful! :)  

Also, any other advice or tips would also be appreciated... for example, I'm guessing that the Rescue partition just does an image dump if I choose to restore in future, in which case would that destroy my root and swap partitions? If so, then there's obviously no reason to keep the Rescue partition.!

Thanks in advance

---

### Post by tgm4883 on 2007-04-06
I always go with murphy's law, if something can go wrong it will.  So my first suggestion is to backup your existing data.

The reason that it mounts your windows xp partitions is that you can read from them, and in some cases write to them (last I checked, writing is experimental, but always evolving)

I'm not sure how useful the 4GB section would be at the front of your drive (yes, if you restored it would make it factory fresh)  You could move it, or set up a lvm.  I guess it depends on if you have a windows MCE cd or not.  I'd leave it alone, but just because it's more work then I think it's work (I use a desktop with 200GB of space and have a 1 TB Fileserver, so 4 GB is nothing to me, but you may really need it.  YMMV)

It has been awhile since I installed a dual boot setup so Im not sure what you need to do with the installer and the extra partitions.  Give it a while, and if someone else doesn't come along then I will throw one together real fast and see what happens.

---

### Post by petit.padavoine on 2007-04-06
next to each partition you want to mount, there's a reformat tick box. as long as the ones next to your rescue and windows partition aren't ticked, you can go ahead.

---

### Post by Jdoki on 2007-04-06
Thanks for the advice.  Have gone ahead with the install, and am now using Ubuntu!! :)  everything seems fine!

Particularly liking what appears to be more 'effortless' resource management when switching between apps etc- no more waiting as I Alt-tab between apps; and the faster boot up time is just what I wanted.

One word on the installer... Any mention of losing data can be a bit daunting (even with backups), so it'd be nice if there was a bit more help/info/hand-holding on those last couple of screens to reassure the user, especially when going for a multiple partition set up with Windows.

All the best

Thanks again

---

