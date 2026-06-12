---
title: "Why does Ubuntu 14.04 change macbook pro 11,5 mbr to hybird?"
date: 2016-05-08
forum: Apple Hardware Users
---

### Post by Robert_Jackson on 2016-05-08
Disk is scrubbed. EFI and MBR is created. NTFS primary partition is build.
Windows is loaded EFI
Ubuntu is loaded live mode EFI.
When using Ubiquity to install Ubuntu and we create / and swap partitions.
As soon Ubiquity commits the partition changes ... it modifies the MBR to be hybrid?
Why Why Why?

---

### Post by Robert_Jackson on 2016-05-08
Could ubiquity be getting tripped up by MacBooks uefi version 1.1 and think it needs to create hybrid? 

Most uefi PCs probably return 2 or higher now? Maybe this world not get caught then in testing on PC side?

---

