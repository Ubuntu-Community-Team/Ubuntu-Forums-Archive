---
title: "Cloning a drive with MacOSX Yosemite and Ubuntu"
date: 2015-06-18
forum: Apple Hardware Users
---

### Post by mfox on 2015-06-18
I have a 2009 Mac mini set up as a dual boot with Yosemite and Ubuntu 15.04; the boot loader is rEFind. The internal drive is a 500 gb HD, and I bought a 500 gb SSD that I want to use to replace the slow HD. I have an external enclosure for the SSD and I want to start by cloning the internal drive before replacing it. (I have an enclosure that I can put the SSD in and it can be attached to the mini through either Firewire 800 or USB 2.) The Mac partition is HFS+ and there is also a recovery partition. Ubuntu is on one ext4 partition and there is a swap partition as well. Is it possible to do a bit by bit copy of the whole drive with either Clonezilla or dd and if so, will the drive be bootable? Or do the Mac and Linux partitions have to be done separately and the boot loader reinstalled? Alternatively, I have a Mac utility called Carbon Copy Cloner - will it make a bootable bit by bit copy of the drive, and will it preserve the partition structure?

---

### Post by mfox on 2015-06-20
I managed to figure it out, and although this might not be the most efficient way, here is what worked:
(1) Put SSD in external case
(2) Use Clonezilla or any other Unix formatting utility to replicate the partition structure of the source disk (in this case, but source and target are same size).
(3) Use Carbon Copy Cloner (CCC) to clone the Mac partition
(4) Use Clonezilla to do a partition to partition clone for the Linux partition
(5) Use gparted from the source disk to format the swap drive of the SSD
(6) Install the SSD inside the computer

Note that one thing I hadn't tried was a disk to disk clone using the 'dd' Unix utility. It may have worked, and it would have covered steps 2-5 if it did. I was worried that it wouldn't have 'blessed' the Mac partition of the target disk (SSD), whereas I knew that CCC would do that. (Note that the clone of a Mac partition has to be 'blessed' to be bootable.) Even if 'dd' alone didn't work, odds are that it would have succeeded in duplicating everything except the 'blessing' in one move, leaving me only to run CCC afterwards. I'll try that the next time.

---

### Post by este.el.paz on 2015-06-23
@mfox:

Thanks for the followup and way to figure it out.  For my dual and triple boot systems I also use CCC to clone the OSX, but my extHD are also multi partitioned and since it seems like the various linux systems I've used lately seemed to have "issues" after awhile, it's just easier to do the fresh install than to try to clone or dd it . . . as you say OSX needs to be "blessed" to be able to boot . . . but interesting idea about running CC after the "dd" . . . might be faster???  CCC is definitely a handy app/tool.

e..

---

