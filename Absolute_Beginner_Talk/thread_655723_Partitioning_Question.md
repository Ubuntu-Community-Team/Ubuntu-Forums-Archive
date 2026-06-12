---
title: "Partitioning Question"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Scott-271 on 2008-01-01
Ok, I have two hdd's:

**hda - 40gig**
[LIST]
[*]hda1 - win2k - 17g
[*]hda2 - /home - 21g(not full)
[*]had3 - swap - 1g
[/LIST]
**hdb - 20gig**
[LIST]
[*]hdb1 - Xubuntu - 5g
[/LIST]

I finally made the jump and wiped the win2k partition. I want to keep hdb for various OS's, and resize hda so it is completely /home and swap. When I run the GParted live cd, I can only decrease the size of /home, not increase it - which is what I want to do.

My questions are:

Is there another way for me to do this?
Do I need to save everything to the spare space on hdb, wipe hda clean and start from scratch?
If I need to save everything to the spare space, how do I go about it? All it really is, is some music and my Firefox settings that I'm worried about.

Thanks,
Scott

---

### Post by gilf on 2008-01-01
When you say that you "wiped" the win2K partition, did you delete it in Gparted so that it is now "free space", or did you try to retain the partition (which is formatted NTFS) and merely wipe out the data?

I believe that you will need to delete that partition in Gparted in order to grow your /home partition in that direction.

Gparted should be able to do this -- I'm sure I've grown partitions in the past -- it needs to know which direction you want to grow (before or after the partition) . Make sure you've set that right, or it won't allow you to grow into your existing swap, and you might not notice that it WOULD allow you to grow the other way (assuming it is free space.

Be SURE of course that you have backed up all of the partitions you want to save on this disk before making any changes to partition structure.

---

### Post by blueridgedog on 2008-01-01
You will also need to unmount the partition before you can resize it.

---

### Post by Scott-271 on 2008-01-01
I completely deleted the windows partition; it is now unallocated, free space.

How do I get Gparted to let me expand/grow in that direction? Currently, it only let's me reduce the size of /home.

---

