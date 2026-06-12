---
title: "Upgrading hard drive; LVM question"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by sdfsqwe on 2008-02-29
I had Fedora 8 installed on my laptop and I'm upgrading the hard drive
to a larger one and switching to Ubuntu.

I'm not able to figure out how to transfer files to my new hard drive. I stuck
the old drive into a hard drive enclosure and when I do fdisk -l, I get:

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15f315f3

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 3917 31457280+ 7 HPFS/NTFS
/dev/sdb2 3918 6527 20964825 b W95 FAT32
/dev/sdb3 6528 6552 200812+ 83 Linux
/dev/sdb4 6553 14593 64589332+ 5 Extended
/dev/sdb5 6553 14593 64589301 8e Linux LVM

I've tried doing:

vgchange -a y
vgscan
lvs

but I'm not sure how to do this exactly. Could somebody
please help me?

Thank you.

---

### Post by justleen on 2008-02-29
i havent tried adding an existing LVM, but ill give it a go..

im assuming, if you now do a vgs or vgscan it wont display any info?
```

$ lvm vgs
  No volume groups found

```

think you need to add /dev/sdb5 as a device for lvm to use, before you can see it
wheter you can see the disks in the lvm, i dunno...

---

