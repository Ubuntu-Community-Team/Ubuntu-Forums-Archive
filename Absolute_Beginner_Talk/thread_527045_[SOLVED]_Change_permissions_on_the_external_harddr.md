---
title: "[SOLVED] Change permissions on the external harddrive"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by chr on 2007-08-16
hello,

i have an external harddrive, which works fine on my windows partition, but when i work with ubuntu (what i do most of the time now) i can't change it to have a read-write permission.

what can i do to change this so i can save and delete files on this external harddrive.

best regards

chr

---

### Post by gn2 on 2007-08-16
If it's formatted in NTFS you'll need ntfs-3g and ntfs-config both available through Synaptic.

---

### Post by chr on 2007-08-16
yes it is formatted in NTFS. 

ntfs-3g and ntfs-config are extra packeges i need to install?


chr.

---

### Post by gn2 on 2007-08-16
> **chr said:**
> yes it is formatted in NTFS. 

ntfs-3g and ntfs-config are extra packeges i need to install?


chr.

Yes, they are in the repositories and can easily be added through Synaptic.

---

### Post by chr on 2007-08-17
i have now installed those packages, but i still don't now how to change the permissions so that i can save and delete files on my external hard drive.

chr.

---

### Post by taurus on 2007-08-17
You need to unmount your ntfs first.  Then, remount it using ntfs-3g so you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by chr on 2007-08-17
cheers mate!

it worked for me. i can read-write now.

best regards

chr.

---

### Post by gn2 on 2007-08-17
> **taurus said:**
> You need to unmount your ntfs first.  Then, remount it using ntfs-3g so you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Excellent link, but for a beginner it falls down at the Configuration section, where under "The automatic way" it says this: 
"If your NTFS partitions are not yet configured, it will ask you to choose a name that will be use as mount point. Just put the name you want."

 A beginner probably won't know:
a: If the NTFS drives are configured or not.
b: what a mount point is
c: what name to put


When writing these help pages the authors should bear in mind that the target audience may have no knowledge of Linux whatsoever.

When I started using Ubuntu it was this kind of assumed level of knowledge that forced me into using first Easybuntu then Automatix.

The Automatix NTFS mounter just makes NTFS drives work with no user intervention required.
OK, there are drawbacks, but at least it works.....

Sits back and awaits anti-Automatix FUD......

(I don't use AX anymore and have removed the link to it from my sig)

---

