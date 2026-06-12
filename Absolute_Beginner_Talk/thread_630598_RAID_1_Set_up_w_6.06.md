---
title: "RAID 1 Set up w/ 6.06"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by mrhinman on 2007-12-03
Here's what I've got.  I've set up my HP box with Dapper Drake 6.06 Server.  It's strictly a server, and not used as a workstation, although I've installed the GUI for ease of use.

The box has a 200 GB SATA drive installed and I can purchase another identically cheaply and easily.  To add the drive and make a RAID-1, will I lose my data, or will it automatically mirror it?  How do Iactually accomplish going from one drive to RAID-1?

Can anyone provide any web links or forum links that could guide me in this respect?

---

### Post by speed145a on 2007-12-03
are you using a raid controller such as a 3ware or just motherboard SATA?  this will change which tutorial to point you to


everything I have used to create RAID arrays have required a complete wipe of each drive placed into the array.

---

### Post by mrhinman on 2007-12-03
> **speed145a said:**
> are you using a raid controller such as a 3ware or just motherboard SATA?  this will change which tutorial to point you to


everything I have used to create RAID arrays have required a complete wipe of each drive placed into the array.

It's motherboard SATA.  A wipe, eh?  That scares me.. a lot.  I'd have to buy 2 hard drives and then copy from one drive to the RAID, probably... unless there's a better way.

---

### Post by umattu on 2007-12-03
If you plan on using the software RAID 1 feature in the dapper install, you WILL have to wipe the drives.

When you set up the partitioning, you have to mark the partitions to be used as a RAID device.

---

### Post by speed145a on 2007-12-03
> **mrhinman said:**
> I'd have to buy 2 hard drives and then copy from one drive to the RAID, probably... unless there's a better way.

or you could backup to something else like an external drive (maybe borrowed) or another computer via LAN

---

