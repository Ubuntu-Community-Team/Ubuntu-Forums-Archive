---
title: "[SOLVED] Complex partition help"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-04-13
I'm trying to partition a large hard disk as an upgrade for my desktop machine, but GParted won't seem to let me do it. I thought I'd lay out how I'd like the drive split up, and hope that one of you out there could suggest how to make it happen.

Here's what I have in mind:

Partition 1: NTFS (for XP)
Partition 2: NTFS (for Vista)
Partition 3: ext3 (for Ubuntu)
Partition 4: ext3 (for exploring other *nix OSes)
Partition 5: fat32 (to store media; formatted as fat32 so that all installed OSes can read/write it easily)
Partition 6: SWAP (for obvious reasons)

In GParted, I can get the first four done, but when I hit "new" to make the fifth partition, it says something about how it can only create four primary partitions. I'm not sure what else to do. Can this be done on the command line using fdisk? I'd prefer to use a GUI, if possible.

Thanks for helping!

---

### Post by original_jamingrit on 2008-04-13
If you can only create four partitions, make your fourth one an 'extended' partition.  You can create up to 24 'logical' partitions inside that.  This can be done with gparted.  The problem is that if you install another OS to that, it won't be bootable.  I suggest keeping the Ubuntu partition as bootable, because you'll be able to boot OS #4 from GRUB.  See 'man grub' or ask for help when you want to try installing your fourth OS.  

So, you can set your partitions up like this: (replace hda with sda for SCSI instead of IDE)
Primary [hda1]  Vista
Primary [hda2]  XP
Primary [hda3]  Ubuntu [mark this as bootable]
Extended [hda4]  Extended partition  (Use all remaining space for this)
Logical [hda5]  ext3 for OS #4 (inside extended)
Logical [hda6]  fat32 store  (inside extended)
Logical [hda7]  swap  (inside extended)

good luck!

---

### Post by doctorbighands on 2008-04-13
Worked like a charm! Thank you!! :)

---

