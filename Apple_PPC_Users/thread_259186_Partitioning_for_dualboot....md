---
title: "Partitioning for dualboot..."
date: 2006-09-17
forum: Apple PPC Users
---

### Post by SixtyFo on 2006-09-17
I was trying to resize my osx partition to make space for a linux boot, but it gives me and error that data relocation has failed. I did a bit of searching and I think the filesystem may be corrupted.

I'm new to all this, and I don't really know whats going on... but does anyone know how to repair the filesystem?

---

### Post by ristosu on 2006-09-17
Maybe you have to turn off journalling in OS X, because Linux won't modify the filsesystem otherwise.

---

### Post by SixtyFo on 2006-09-17
Journalling was disabled. I tried again with the gentoo livecd and it started the filesystem shrink, but gave me read errors at 62%, always starting with the same sector.

---

### Post by SixtyFo on 2006-09-17
This is the error I get from GNU Parted:

hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114505295, hight=6, low=1384199, sector=114505232
ide: failed opcode was: unknown
end_request: I/O error, dev hda, sector 114505232
Buffer I/O error on device hda, logical block 14313154

This continues for another 8 different sectors then it gives me:

Error: Input/Output error during read on /dev/hda
Retry/Ignore/Cancel?_

What does this mean exactly? And how do I fix it?

---

### Post by ristosu on 2006-09-17
I'm afraid there is physical damage on your hard disk. The blocks in question should be marked as bad ones, and not be used. Linux can do this, while formatting its own partition; not sure about OS X. If I were you, I would try to check the disk from OS X (fsck /dev/disk...).

---

### Post by SixtyFo on 2006-09-17
Thanks for the info. Funnily enough fschk says that the volume appears to be ok. I guess theres no way around but to wipe the drive and start over :rolleyes:

---

