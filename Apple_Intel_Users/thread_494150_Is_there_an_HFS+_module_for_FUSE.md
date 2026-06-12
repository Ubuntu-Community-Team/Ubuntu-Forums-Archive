---
title: "Is there an HFS+ module for FUSE?"
date: 2007-07-06
forum: Apple Intel Users
---

### Post by Egils on 2007-07-06
Hi,

does anyone know if there is an HFS+ module for FUSE or if there are plans to make one? NTFS read-write support with NTFS-3G has been so useful. An equivalent for HFS+ would be the icing on the cake!

Egil.

---

### Post by cyberdork33 on 2007-07-06
read-write support for hfs is in the linux kernel.

---

### Post by ronocdh on 2007-07-07
> **cyberdork33 said:**
> read-write support for hfs is in the linux kernel.
Just remember to disable journaling in OS X if you're trying to share across partitions. Ubuntu works very well with HFS+ non-journaled, except for a few permissions issues, which can easily be overridden with root privileges.

---

### Post by cyberdork33 on 2007-07-07
> **ronocdh said:**
> Just remember to disable journaling in OS X if you're trying to share across partitions. Ubuntu works very well with HFS+ non-journaled, except for a few permissions issues, which can easily be overridden with root privileges.

Just like any other linux filesystem that has a separate OS installed on it.

---

### Post by Egils on 2007-07-07
I should have been more specific in my first post - I was thinking that it would be nice to have read-write access to an HFS+ partition without having to disable the journaling. But maybe maintaining the journaling wouldn't be a strong enough incentive for someone to develop such a module, considering the support that already exists (and the likely performance disadvantage).

---

