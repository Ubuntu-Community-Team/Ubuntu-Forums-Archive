---
title: "MBR problems after inserting a new HDD"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by andy_blah on 2008-03-24
I have tried to add a new IDE HDD, I pluged in the IDE cable and the power cable. After the boot I have checked the BIOS and it was listed as a master HDD (hda), and the old HDD was before the slave HDD (hdb - hdb1+hdb2). After I try to boot into Ubuntu it give me a OS error and prompts me to insert the system disk. I insert the Ubuntu CD and got into the Live session. I think it`s a problem with GRUB as it is not loaded at the start-up. What should I do to fix this?(the partition with Ubuntu installed is hdb1) 

Thank-you in advance,
>-Andy-<

---

### Post by LowSky on 2008-03-24
switch the two hard drives, make the new one slave and the old one master (change the little jumper pins on the hard drives, and switch the cables connecters) problem solved.

---

### Post by waspbr on 2008-03-24
I would recommend you burn yourself a supergrub CD

---

### Post by andy_blah on 2008-03-24
@LowSky: The old HDD was slave before, as it is now.
@waspbr: I donnot have any empty CD at the moment. Is it possibile to be installed on a floppy?

---

### Post by ajgreeny on 2008-03-24
I am a bit muddled about what your problem is. Do you gat to a grub menu and then not able to boot anything or does the startup say "starting grub" and then abort completely?> What should I do to fix this?(the partition with Ubuntu installed is hdb1) So what's on hda, which I think is your new disk?  Is windows there or is it still empty, because your MBR was probably on the old disk, now removed, so will need reinstalling when you reinstall windows.  Then you can get grub back, but first you need an MBR to work on.

If I've got it all wrong and misunderstood your situation, come back again with more info.

---

