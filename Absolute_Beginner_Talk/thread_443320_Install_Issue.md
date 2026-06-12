---
title: "Install Issue"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Firewalker138 on 2007-05-14
Getting tired of all the issues with Windows and decided I would finally try out Linux.  I have installed Ubuntu but every time restart the computer it just loads into Windows and doesn't even give me any options.  Here are the specifics:

1)  My PC currently has 2 HDD.  1 - 120GB IDE and 1 - 120GB SATA.
2)  Windows is installed on the SATA.  I adjusted the partition sizes.  Partition 1 is the Windows OS partition, partition 3 now my SWAP partition, and partition 4 is my Linux partition (ext3).
3)  I installed Ubuntu (Feisty Fawn) to partition 4 and assigned the mount point to "/".

For some reason it won't even give me the option to boot into Ubuntu.

---

### Post by dstew on 2007-05-14
It sounds like the grub boot loader has not been installed. Do you recall if you installed it or not (usually the option presents itself at the end of an ubuntu installation session)?

Is your Windows Vista or XP (or something else)?

---

### Post by Cypher on 2007-05-14
Grub might be installed to the wrong HD. When using IDE and SATA in the same machine, which HD is the boot HD??

---

### Post by Firewalker138 on 2007-05-14
I am running Windows XP.

I'm not sure which HDD is my boot drive ... how do I find that out?

---

### Post by Cypher on 2007-05-14
The boot order is usually controlled in BIOS. I've only never had SCSI/IDE, full-IDE or full-SATA configurations, so I don't know how a IDE/SATA configuration will look like in the BIOS..

---

