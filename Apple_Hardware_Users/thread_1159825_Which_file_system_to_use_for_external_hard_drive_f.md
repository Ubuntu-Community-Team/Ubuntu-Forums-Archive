---
title: "Which file system to use for external hard drive for MAC and ubuntu access?"
date: 2009-05-15
forum: Apple Hardware Users
---

### Post by eneloop on 2009-05-15
I have an external hdd that is partitioned and uses the hfs+ file system. I can read and copy files from the hdd to the ubuntu pc, but cannot execute nor write from the hdd. 

Using chown/chmod/sudo nautilus/mount hasn't worked.

Which file system is best for an external hdd that uses both MAC and ubuntu?

---

### Post by maflynn on 2009-05-15
ASFAIK your only option is FAT32, OSX does cannot access EXT partitions and as you noticed Ubuntu can only read from HFS+ partitions.  Both OS's can read/write to FAT so that will give you the read/write access you require

---

### Post by timcredible on 2009-05-15
fat32

---

### Post by gotgenes on 2009-05-15
I've been using HFS+ non-journaled case sensitive. Create the partition using Disk Utility in OS X. You'll need to install the hfsplus and hfsprogs programs in Ubuntu. Then plug in the external drive, and it should read/write. I get corrupted headers in the filesystem from time to time. Use the disc repair option in OS X Disk Utility to fix these.

It's important that you use non-journaled. HFS+ journaled write support hasn't been added in Linux yet.

---

### Post by kanikilu on 2009-05-15
> **gotgenes said:**
> I've been using HFS+ non-journaled case sensitive. Create the partition using Disk Utility in OS X. You'll need to install the hfsplus and hfsprogs programs in Ubuntu. Then plug in the external drive, and it should read/write. I get corrupted headers in the filesystem from time to time. Use the disc repair option in OS X Disk Utility to fix these.

It's important that you use non-journaled. HFS+ journaled write support hasn't been added in Linux yet.

+1 - I'm still awaiting the day I can write to journaled HFS+, but for now, like you, I use non-journaled HFS+ on my 1TB external USB drive with no major issues.

The only problem I've run into was when the drive was accidentally removed in Ubuntu without unmounting first. When I tried it again it would only mount read-only. In that case I had to plug it into my Macbook, eject it, and then it worked fine again in Ubuntu. I think this is the same if you use NTFS, though, so I don't think it's specific to HFS+.

---

### Post by buttertoad on 2009-05-15
What about EXT2?

[http://ext2fsx.sourceforge.net/]("http://ext2fsx.sourceforge.net/")

---

### Post by eneloop on 2009-05-16
> **gotgenes said:**
> I've been using HFS+ non-journaled case sensitive. Create the partition using Disk Utility in OS X. You'll need to install the hfsplus and hfsprogs programs in Ubuntu. Then plug in the external drive, and it should read/write. I get corrupted headers in the filesystem from time to time. Use the disc repair option in OS X Disk Utility to fix these.

It's important that you use non-journaled. HFS+ journaled write support hasn't been added in Linux yet.


Thanks! I finally got it to work.

I have an hfs+ non-journaled non-case sensitive partition on my external hdd as well, but wasn't able to write to it until I installed the 'hfsplus' and 'hfsprogs' programs.

---

### Post by cyberdork33 on 2009-05-16
> **buttertoad said:**
> What about EXT2?

[http://ext2fsx.sourceforge.net/](http://ext2fsx.sourceforge.net/)
that is hit-or-miss with that driver (ext3 works just as good/bad with it). Development stopped long ago too.

---

### Post by GadgetFreak on 2009-09-18
> **gotgenes said:**
> I've been using HFS+ non-journaled case sensitive. Create the partition using Disk Utility in OS X. You'll need to install the hfsplus and hfsprogs programs in Ubuntu. Then plug in the external drive, and it should read/write. I get corrupted headers in the filesystem from time to time. Use the disc repair option in OS X Disk Utility to fix these.

It's important that you use non-journaled. HFS+ journaled write support hasn't been added in Linux yet.


gotgenes,

Have you ever experienced data loss when sharing your external HD with both Mac OS X and Ubuntu? I'd really like to have a single partition on my external HD so that I can use the space as needed from both operating systems without worrying about partition sizing. Of course, integrity is critical here; I'm okay with the occasional header corruption provided that I never find myself not being able to fix it. 

Planned setup:
- Dual boot, Snow Leopard and Ubuntu 9.04 server, Mac Mini (2nd gen) (this config already working)
- HFS+ with journaling disabled on external firewire 1TB drive
- hfsplus and hfsprogs to be installed into Ubuntu server

Thanks for any feedback.

---

