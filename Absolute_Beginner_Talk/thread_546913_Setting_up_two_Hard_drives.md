---
title: "Setting up two Hard drives"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by dhavalbbhatt on 2007-09-09
I have been using Ubuntu for a while now - used to have an old machine on which I had 1 SATA drive on which I had Ubuntu and another IDE drive on which I had Windows XP home. The IDE drive was the primary drive and the DVD-ROM drive was the secondary drive on that system. That system used to dual boot. I recently build a new system with the same old hard drives (1 SATA drive and 1 IDE drive) and re-installed Ubuntu on the SATA drive. I also made the IDE the secondary drive, with the DVD-ROM drive as the primary drive. I am also moving away from Windows completely, and I did install Ubuntu on the IDE drive as well. My problem is that though I can mount the IDE drive when I work in my SATA drive, I can't seem to write to the IDE drive at the same time. In addition, I don't get a dual boot screen at the beginning - I am not sure whether I should get a dual boot, since both the drives have the same OS. 

All help is greatly appreciated.

Thanks,
DB

---

### Post by mendingo84 on 2007-09-09
you don't get a boot choice because your SATA has a bigger boot priority than that of the IDE drive and on your SATA you only have Ubuntu installed. For the second issue, if you are trying to write to ntfs ( the Windows filesystem ) you have to install a small application that allows you to do this ( it called smth like "ntfs-xxx" )

---

### Post by dhavalbbhatt on 2007-09-09
Thanks for the quick reply. My IDE drive does not have NTFS, it has Ubuntu installed on it as well, which is why I can't understand why is it that I can't write to the IDE drive when I am logged into the SATA drive.

DB

---

### Post by vanadium on 2007-09-09
You only can write to a drive (as a user) when you have permissions! Check the permissions first and change them (acting as root) if needed.

---

