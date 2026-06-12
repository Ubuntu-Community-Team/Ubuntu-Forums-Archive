---
title: "ubuntu on a ntfs raid0 array with xp on already"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by RobTi on 2007-04-24
Hi all i have just tried ubuntu from the cd  and would like to give it a try, the problem is current set up is win xp on drive D(made a mistake on a clean install and it installed on D)now i am running  raid 0 array and ntfs if i load cd and tell it to install on drive C which is just where i put all my software installs what would happen.
Failing that i could plug in an extra drive if needed?
Thanks
Robert

---

### Post by BoneKracker on 2007-04-24
Please clarify.  It's hard to read what you wrote.

I am guessing from what you said that you have a two-disk SATA RAID-0 array, that you then partitioned that in two (seen as C: and D: from within Windows).  You have Windows XP installed on D:, and you have some miscellaneous programs that you use in Windows installed on C:.

You want to know what will happen if you tell the installer to use C:.

Several problems with that scenario:

a)  You can't install Linux on an NTFS partition.  The partition will have to "re-formatted".

b)  Installing onto any partition(s) completely re-formats them -- all data will be lost.

c)  I don't believe the Ubuntu installer can install to a SATA RAID array.  SATA RAID (or "fakeRAID") is something the PC builders came up with to make up for the fact that Windows doesn't have any capability of its own to map multiple drives to a RAID array.  Linux has this capability built in.  There is a howto on the ubuntu wiki that tells how to install to fakeRAID array, but I'm not sure it's been updated to take into account possible changes in Ubuntu 7.04.

So you need to get your "programs" off that partition or re-size it.  You need a free partition to put Linux on.  And if that partition happens to be on a fakeRAID array, you can try the new installer (maybe it can handle fakeRAID now), or you can look at the fakeRAID howto.

---

