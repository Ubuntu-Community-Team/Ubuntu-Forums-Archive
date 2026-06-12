---
title: "Shared external harddrive across OSX, XP, and Ubuntu"
date: 2007-09-03
forum: Apple Intel Users
---

### Post by subferno on 2007-09-03
I have a MacBook Pro (triple boot with OSX, Ubuntu, and XP).

Can I purchase a USB harddrive that is shareable by all three of those OS's? I remember reading something about how OSX uses the HFS+ file system while XP uses NTFS, therefore different. Is the only way to share the single harddrive is to format it as a FAT32?

What if I decide to create seperate partitions for each of the OS on the external harddrive? Is it possible?

Thanks

---

### Post by ivesjd on 2007-09-03
You can share across all three. It takes some work though. You could use Fat 32 which would take no work since everything supports it. However, if you will have files over 4gbs fat32 will not work. What may be a strange suggestion is to use Ntfs. Since there is ntfs-3g for OS X. There is also ntfs read/write support for Linux. Hope that helps.

---

