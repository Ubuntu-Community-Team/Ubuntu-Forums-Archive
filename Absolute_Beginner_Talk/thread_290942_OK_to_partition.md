---
title: "OK to partition?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-11-01
So I am trying to help a friend get regular Ubuntu on his computer and get rid of Xubuntu. I downloaded and burnt the alternative .iso file, and am trying to partition. But... I'm not sure if I should go through with it.

He has a crap load of stuff on his computer, and wouldn't it just be awful if he lost it all because of me?

Anyway, after the partitioning questions and it asks what size, it sits there for a while and asks me this:

```
[!!] Partition Disks

If you continue, the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 IDE1 master (hda)

The following partitions are going to be formatted:
 Partition #3 of IDE1 master (hda) as ext3
 Partition #6 of IDE1 master (hda) as swap

Write the changes to disk?
```

Then it asks if I want to go back, select yes, or no.

Now, for one question: If I did press yes, would all of his current data be erased? And if I partition, can I pull his files from Xubuntu onto Ubuntu and get rid of Xubuntu?

Please note: I am well aware of the guides this one guy posted to use aptitude and to get "pure GNOME" and stuff. I've done this before and it really isn't all that pure, and my friend would appreciate Ubuntu instead of mixed software from Xubuntu.

Thanks in advance!

---

### Post by mattskr on 2006-11-01
It depends on how many partitions are on his drive and which ones you will be partitioning.

Partitioning WILL ERASE all the data on those partitions if that's what you are asking.

I would recommend backing up your important files before doing any major change to your system. An external USB hard drive would be the easiest way to back everything up.

---

### Post by podunk on 2006-11-01
Back it up. :-) I know windows back up programs are slow and kludgy - but even if you do everything right the worst could happen anyway. The power could flicker for instance.

If you have a USB drive handy with a FAT32 partition you can use the Ubuntu live CD to drag and drop the My documents folder on it (c:\Documents and Settings\what_ever_your_name_is\My Documents) and it won't take but 20 minutes.

Back when I had windows data to worry about I <blush> used the disk management tools in XP to delete my Linux partitions, then let the install CD install into the largest free space.
Start>Settings>Control Panel>Performance and maintenance>Administration>Computer management>Storage>Disk management

phew! The CLI is faster! :)

---

