---
title: "can't install 6.10 on Dell computer"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Tom_the_penguin on 2007-03-13
Hello,
I am trying to install Ubuntu 6.10 on my Dell Dimension 8400. The target disk is an external USB drive (I have 2), so I can keep windows XP on the internal drive. While running the Ubuntu install I get the choice of partitions:
/dev/sda: SCSI 1
/dev/sdb/SCSI 7
/dev/sdc/SCSI 5
and choosed sdb - partition and use all disk
it said the GRUB would be installed on (HD0)
I get this message when installing
"the ext3 file system creaction in partition #1 of SCSI 7 (0,0,0) (sdb) failed"
Tried several times but no luck. Any ideas?

Also it seems that there is a problem with the bootloader - I get an error message 21 from Grub 1.5 (it's related to no disk found) - So I can't load either Windows XP or Ubuntu!
And since it's a Dell with no startup disk I can't even do fixmbr from Windows...


Since it's a Dell computer it has already some partition on the internal drive (used for backup/system) - is this confusing the bootloader? (partition say sda1 fat 16 sda2 ntfs sda3 fat32) 
many many thanks - no home computer since a week :-(

---

### Post by mahy on 2007-03-13
> **Tom_the_penguin said:**
> 
I get this message when installing
"the ext3 file system creaction in partition #1 of SCSI 7 (0,0,0) (sdb) failed"
Tried several times but no luck. Any ideas?

Also it seems that there is a problem with the bootloader - I get an error message 21 from Grub 1.5 (it's related to no disk found) - So I can't load either Windows XP or Ubuntu!
And since it's a Dell with no startup disk I can't even do fixmbr from Windows...

Since it's a Dell computer it has already some partition on the internal drive (used for backup/system) - is this confusing the bootloader? (partition say sda1 fat 16 sda2 ntfs sda3 fat32) 
many many thanks - no home computer since a week :-(

You can try installing Ubuntu on another external drive (coz you have two of them) or choose a different filesystem. ReiserFS is my filesystem of choice.

I don't quite understand why you have probs with GRUB. The filesystem creation failed for you, so how come GRUB got installed?? Bootloader is the last one in order.

It's always bad news if you don't have a windows cd, but you can use any other (retail) xp cd, provided it recognizes the disks, right? (nLite -- [http://www.nliteos.com](http://www.nliteos.com) -- can help you with that) You don't need an OEM cd.

---

### Post by Tom_the_penguin on 2007-03-13
Cheers... I have the GRUB because as Ubuntu was not installed I tried OpenSUSE (I get the same problem in OpenSUSE).
Can I download nLite and use it as a bootable CD?

---

### Post by mahy on 2007-03-13
> **Tom_the_penguin said:**
> Cheers... I have the GRUB because as Ubuntu was not installed I tried OpenSUSE (I get the same problem in OpenSUSE).
Can I download nLite and use it as a bootable CD?

nLite is not a bootable CD. It's a piece of software for "slipstreaming" additional drivers and stuff into windows CDs. You need a windows cd in the first place. Go ask your laptop vendor for something. If they refuse to cooperate, borrow one from a friend (just for MBR repair of course).

---

### Post by mahy on 2007-03-13
However, the best option would be to move all your backed-up stuff onto external drives and install Ubuntu to the internal one. It very shortsighted to install system to an external drive, because if you unplug it, you won't be able to boot any system. Yes, i know GRUB Stage 1 resides in the MBR (and that's on an internal drive), but stages 2 and 3 have to be loaded from some Linux partition (i.e. your external drive). Not a good idea!

---

