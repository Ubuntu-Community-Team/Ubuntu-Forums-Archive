---
title: "Can't mount NTFS partition. ntfsfix?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by DarthSudaka on 2006-11-05
Hi!
I`m having trouble with my windows partiton, I don`t know if it`s because I tried to use ntfs-3g to have write support in linux or what. Thing is I can`t mount it, neither with ntfs-3g nor using the backup of fstab.

When I try to manually mount it I get:
Failed to mount '/dev/disk/by-uuid/....': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.by-uuid/....'
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.


I can`t boot Win, so should I try ntfsfix?? I read that it may causa data loss, is that right??

thanks a lot!

---

### Post by givré on 2006-11-06
> **DarthSudaka said:**
> 
I can`t boot Win, so should I try ntfsfix?? 
Why can't you boot on windows
> **DarthSudaka said:**
> I read that it may causa data loss, is that right??

Of course not.

---

### Post by dyrer on 2006-11-16
Am having same problem too, after vista install
Now cannot install any windows version to this hard drive, this hd is separated to two ntfs partitions

---

