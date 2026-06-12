---
title: "what disklabel to put?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-10-17
320 gig (IDE) usb drive.
gparted asks to put a disklabel so i just want to know which one to put?
is GPT ok? 
on GNU parted page it says that this should be used with new filesystems like ext2, ext3, xfs etc. i want to put ext3.

---

### Post by monktbd on 2006-10-17
use whatever you like but use something easy to remember because it will always be mounted with this name.

if you do not give a label then it might happen that the mount points change when you have more than one external harddisk partition mounted which is not very practical when e.g. storing music on it and having a library point there.

so choose any you want that makes sense for you :).

---

### Post by zekopeko on 2006-10-17
i think you misunderstood. disklabel is another name for partition table.
reading some post here revealed that msdos is fine but i want to know if i use GPT (GUID partition table) am i going to have problems since this is a part of the EFI (the thing replacing the BIOS on future motherboards) and my motherboard is and old nForce2?

---

