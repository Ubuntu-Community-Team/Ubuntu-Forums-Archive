---
title: "Uninstall Ubuntu from Powerbook G4"
date: 2006-11-24
forum: Apple PPC Users
---

### Post by snl on 2006-11-24
How can I uninstall Ubuntu from Powerbook G4 and re-format Ubuntu partition back to Powerbook HFS+? I am worrying about bootloader (yaboot).

Thank you

---

### Post by seatea on 2006-11-24
I think you can use the Live CD to delete the Ubuntu partition and then format it as HFS. The Ubuntu Live CD's gparted does not format HFS+. Gparted will also resize a partition. Don't change partition  sizes  unless you have backed up everything you need to preserve that may be on other partutions on the same  disk. You can  then use Disk Utility from Mac OS X to format HFS+ on the partition.

---

### Post by snl on 2006-11-26
> **seatea said:**
> I think you can use the Live CD to delete the Ubuntu partition and then format it as HFS. The Ubuntu Live CD's gparted does not format HFS+. Gparted will also resize a partition. Don't change partition  sizes  unless you have backed up everything you need to preserve that may be on other partutions on the same  disk. You can  then use Disk Utility from Mac OS X to format HFS+ on the partition.

How do I use Ubuntu Live CD to delete the Ubuntu partition? After I have deleted Ubuntu partition, what will happen to the bootloader? How to reverse back to use Mac OS X's bootloader?

How to use Disk Utility to format HFS to HFS+?

Thank you.

---

### Post by EuroCity on 2006-11-26
Wouldn't it be much easier to just use the Mac OS X (or PowerBook) install/restore CD(s)? It should be enough to open Disk Utility from within this CD and reformat the whole disk as HFS+ Journaled.

... Ooops: maybe you have an OS X partition that you don't want to wipe and reinstall (didn't think about that). Then, to delete the New World Apple_Bootstrap partition (usually a small 800 KiB-1 MiB one at /dev/hda2), just use the Ubuntu CD (as previously said) and select it from within the GParted interface: then, delete it from there, together with the other Linux partitions (usually / and /swap); the Apple Partition Map (/dev/hda1) should be left as it is, untouched. If the Desktop CD doesn't work, one can always use the Alternate CD.

As for resizing the OS X partition to occupy the full volume, others might know better if it is possible/safe or not.

But why would you want to delete Ubuntu? If there are problems, maybe they will be solved in future releases...

---

### Post by AlphaMack on 2006-11-26
There is a very large thread buried deep somewhere on 'safely' resizing partitions.  Have a look at it.

---

### Post by snl on 2006-11-26
I couldn't format Ubuntu partition to HSF, but manage to format to FAT32. How can I convert FAT32 to HSF+ using Disk Utility?

Thank you.

---

### Post by gramble on 2006-11-27
Hmm. Well, FAT32 certainly isn't the direction that you want to go in, because it's a Windows-only format (though I suppose that it's possible for Mac OS to read it). Not a problem though, you will be wiping this partition and not really "converting" it.

I'm not certain whether Disk Utility will work with individual partitions without wiping the entire partition map--you can give it a whirl, but pay very close attention to the warning messages it gives you and back out if it doesn't appear to be talking about just wiping the one partition. Either way, I would definitely back up.

Disk Utility is the only free tool that I know of that can handle writing HFS+. (I think I may have heard about a command-line utility in 10.4, but I'm not sure.) Other than that, there are a few non-free options, such as iPartition, which works pretty well for me.

Sometimes other distributions' installers will have better or less confusing partitioning tools--Gentoo uses pdisk, I believe, which I like due to its flexibility. However, you really will want to use HFS+ and not HFS (the latter of which I believe pdisk can write) if you are using Mac OS X.

---

