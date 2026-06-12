---
title: "Changing Partition Format"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-06-29
I have two FAT32 partitions (+ 1 for XP). Now Ubuntu checks them every time I boot and booting time is long. I am planning to change them to EXT3 using GParted Live CD or maybe from Ubuntu. Obviously I shall shift the data first, I got backup anyway.

Now after formatting I shall have to edit fstab. Can I just alter the lines for the partitions making them similar to one EXT3 partition I have on same PC ? Is there more to this than what I see ?

---

### Post by skymera on 2007-06-29
i dont think you have to use Live CD for that.
since they are not cruical to you ubnuntu.
what are fat32 for? very old file format

---

### Post by starcraft.man on 2007-06-29
Simple answer is yes, if your model your fstab entries for the two partitions you change to ext3 after your other ext3 partitions it should work, so long as you modify exactly whats needed. I am pretty sure you can turn off the check in the fstab entry though I'm no expert on that... I think its the pass entry, make it 0? Don't quote me, I dunno.

References I did find that look good (and I will be reading later) are these:
[Understanding Fstab]("http://doc.gwos.org/index.php/Understanding_fstab")
[How to Fstab]("http://ubuntuforums.org/showthread.php?t=283131")

IMO its always best to actually know what your doing, rather than emulating what someone else did.

Edit: Lol, skymera fat32 may be old but its still useful. I've bought two USB mass storage drives lately, external ones. Both came formatted with Fat32, I assume for compliance with anyones OS. It's not that useless and is fine for long term storage.

---

### Post by dptxp on 2007-06-29
I use dual boot, the Fat32 ones existed before I installed Ubuntu on my 4th partition.
They have data. I have XP on partition 1.

---

