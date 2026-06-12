---
title: "reinstall advice"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-12-31
Hi,
I've lost /dev/video0 so my webcam won't work, and I'm not getting much help.  So searching for similar problems, someone suggested a reinstall.  So my question is a) should I do this, and b) given that I just followed the instructions in the first place and let ubuntu partition my harddrive as it saw fit, can I re-install without loosing all my data??

please help
Thanks
Tony

P.S. happy new year!!!

---

### Post by lgambett on 2007-12-31
I cannot answer to the question about /dev/video0, but I suggest you - for the next reinstall - to keep your /home and / partition on separate devices (eg /dev/hda1 and /dev/hda2); in this way you can reinstall Ubuntu without losing your data & application configurations.
Happy 2008 !

---

### Post by mikewhatever on 2007-12-31
> **tony.morse said:**
> Hi,
I've lost /dev/video0 so my webcam won't work, and I'm not getting much help.  So searching for similar problems, someone suggested a reinstall.  So my question is a) should I do this, and b) given that I just followed the instructions in the first place and let ubuntu partition my harddrive as it saw fit, can I re-install without loosing all my data??

please help
Thanks
Tony

P.S. happy new year!!!

No. If you reinstall letting Ubuntu take up the whole disk, it will formate the disk erasing your data. If you want to keep it, backup to CDs/DVDs or a separate partition if any. What is your current partition table? Please post <sudo fdisk -lu> output.

---

### Post by tony.morse on 2007-12-31
$ sudo fdisk -lu
[sudo] password for tony:

Disk /dev/hda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000be145

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   973747844   486873891   83  Linux
/dev/hda2       973747845   976768064     1510110    5  Extended
/dev/hda5       973747908   976768064     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 11.5 GB, 11525455872 bytes
255 heads, 63 sectors/track, 1401 cylinders, total 22510656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x93aa93aa

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    22490999    11245468+   7  HPFS/NTFS

---

### Post by mikewhatever on 2007-12-31
So, Ubuntu is on hda, root and swap taking up the whole of the HDD. As I said earlier, formating root will erase its data. Do backup before doing so.

---

### Post by tony.morse on 2007-12-31
ok cheers, I have a usb harddrive for backup (let's hope it's big enough)...

---

