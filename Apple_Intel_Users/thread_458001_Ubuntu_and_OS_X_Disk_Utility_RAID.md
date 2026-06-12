---
title: "Ubuntu and OS X Disk Utility RAID"
date: 2007-05-29
forum: Apple Intel Users
---

### Post by EuroCity on 2007-05-29
I would like to mount a striped RAID array, formatted with OS X 10.4.9's Disk Utility, in Ubuntu 7.04 (I'm still on a PPC Mac, but the question in principle arises also for an Intel Mac): I tried this some time ago, but the two disks of the RAID appeared as separate volumes in Nautilus and in GParted (or QtParted).

Is there a way to make an */etc/fstab* entry for an Apple software RAID volume in Ubuntu?

Linux tools, such as *dmraid* or others, if installed, don't seem to recognise an Apple RAID: or am I wrong?

For example, an ordinary HFS+ Journaled volume would be something like this:

```
/dev/hda3 /media/macosx hfsplus defaults 0 0
```

... to mount it read-only: but what about a RAID formatted with Apple's Disk Utility?

Has someone tried that?

(Of course, all this is also because I want to use the striped RAID primarily in Mac OS X, as a */Users* data volume: so it wouldn't really be too good to format it as a RAID in Ubuntu, probably.)

---

### Post by igloocentral on 2007-05-29
To my knowledge, you can't do that. But who knows, I've been wrong before.

I've never understood the advantage of a striped array - it just gives you one big disk instead of two small ones. Having two small ones has advantages  - especially when one of the drives fails: If a drive fails, the other continues operating. If its part of an array however, you may have a big problem on your hands getting to the data from either one of the drives.

---

### Post by EuroCity on 2007-05-29
First of all, thank you for your answer...

So, if I understand it right, the problem could be an incompatiility between the Mac OS X and Linux ways of formatting the software RAID...?

I'd want to make a striped RAID because I have two identical 250 GB disks on an internal Sonnet Tempo ATA-133 PCI card, and at the same time I have a LaCie Mini 500 GB external backup drive: so, anyway, I would always have a complete backup of all the data! (See also Time Machine in Mac OS X 10.5, for example...) 

The striped RAID gives better and more optimised performance (my G4 is rather old, now!), from what I've read: the PCI ATA card has two independent controllers, so the data can be read and written at a faster rate. Or am I wrong, on this?

My Power Mac G4 also has two 120 GB drives on the single on-board ATA-66 controller: on the master I have Mac OS X, on the slave Linux (with partitions for Fedora, OpenSUSE and Ubuntu).

Essentially, I thought that putting the two bigger drives in a RAID would optimise performance: but maybe this wouldn't be so noticeable? It would also be "cleaner", for with a RAID I could have a single 500 GB /Users drive, while with two separate ones I must have one 250 GB /Users drive and another 250 GB one for my Virtual PC images (aliased or symlinked to the Documents folder on the /Users drive).

But I guess I'll keep the two drives separate, if there's no way to mount them (read-only) in Linux.

IIRC, there's a similar problem with Windows NTFS RAIDs in Linux...

---

