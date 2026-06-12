---
title: "File System Problem"
date: 2006-06-17
forum: Apple PPC Users
---

### Post by Najand on 2006-06-17
I have been trying to install DapperDrake on an iBook G4 for 2 days and I stilll cannot install it. I want to manually partition my harddisk and the automatic partitioning is not a proper way in my case. I was able to reformat HFS+ to 3 partitions of /(root), and 2 swap partitions. However there are issues, that I could not still understand:

1. The file system of Apple_Bootstraper is called New World. I am not a MAC user at all and I don't now the difference between HFS and HFS+ and the Journalized HFS+? Which of these is called "New World"? Should I format the Bootstrap Partition using the MAC Disk Utility or using the DapperDrake Live CD?

2. Again about the Apple_Bootstraper, after formating the partitoin in a suitable file system, how can I make the partition bootable with the GUI install manager of DapperDrake in the Live CD? Or should I use the Mac CD to make a partition bootable? I can remember during old days of Breezy and the Text-Installer of Ubuntu, we could put a boot flag for bootable partitions which I could not find in this new system. Although Swap Flag appears to be created automatically.

3. At the last period of partitioning, is it neccessory to rename the Bootstap to "NewWorld" or "Bootstraper" and make the partitioner to reformat it again?

Is there anyone, here, aware of the solutions of these issues. Any helps are greatly appreciated.

---

### Post by tidris on 2006-06-17
I can tell you a little about that boostrap partition. The type of the partition is Apple_Bootstrap, but its format is actually hfs. The reason why the type is Apple_Boostrap instead of Apple_HFS is to prevent OSX from mounting it and messing with it. For more info see man boostrap.

---

### Post by Najand on 2006-06-17
[QUOTE=tidris]I can tell you a little about that boostrap partition. The type of the partition is Apple_Bootstrap, but its format is actually hfs. The reason why the type is Apple_Boostrap instead of Apple_HFS is to prevent OSX from mounting it and messing with it. For more info see man boostrap.[/QUOTE]

Thank you  very much. With your help and by reading Bootstrap Manual and a few other documentations in Debian, I could finally install Ubuntu on my iBook G4 successfully. But still there is another issue that sounds strange to me. During the  Installation I noticed that the partitioner in the GUI installer (Hmm, Gparted, if I am not wrong) cannot recognize UFS (Unix  File System) which is now an available filesystem for MAC OS X.  However if the installer cannot recognize the filesystem, it cannot recognize that there is any other OS installed there. As a result the Yaboot cannot make a dual boot manager that have the ability to select between Linux and Mac OS X and the CD-ROM drive. Is there solution to install a dual boot consisting of Linux and Mac OS X (with UFS file system)?

---

### Post by tidris on 2006-06-17
[QUOTE=Najand]Thank you  very much. With your help and by reading Bootstrap Manual and a few other documentations in Debian, I could finally install Ubuntu on my iBook G4 successfully. But still there is another issue that sounds strange to me. During the  Installation I noticed that the partitioner in the GUI installer (Hmm, Gparted, if I am not wrong) cannot recognize UFS (Unix  File System) which is now an available filesystem for MAC OS X.  However if the installer cannot recognize the filesystem, it cannot recognize that there is any other OS installed there. As a result the Yaboot cannot make a dual boot manager that have the ability to select between Linux and Mac OS X and the CD-ROM drive. Is there solution to install a dual boot consisting of Linux and Mac OS X (with UFS file system)?[/QUOTE]
You could try editing /etc/yaboot.conf and reinstalling yaboot with the ybin command. See man yaboot, man yaboot.conf, and man ybin for more info.

---

### Post by Najand on 2006-06-19
Thank you very much for your reply. I could manage everything now and everything is perfect now.

---

