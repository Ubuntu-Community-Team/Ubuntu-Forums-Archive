---
title: "Want to format my external as an ntfs fs"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by era86 on 2007-06-18
I have an external hd currently formatted as fat32.  i would like to reformat it as ntfs.  Is this possible?  Any help would be appreciated.  Thank you!

---

### Post by joe.turion64x2 on 2007-06-18
Of course it is possible, you only need to open Gnome Partition Editor (Gparted) (it is in the System > Administration menu, or in System Tools under the Applications menu). There you have to select your external drive, unmount it, and then format it as NTFS (right click the partition).

If you don't have Gparted installed use Synaptic to retrieve it.
Joe.

---

### Post by era86 on 2007-06-18
i do so, but the ntfs option isnt allowed?  do i need any other programs or ibraries for this to work?

---

### Post by orb9220 on 2007-06-18
> Open Gnome Partition Editor (Gparted) (it is in the System > Administration menu, or in System Tools under the Applications menu).

Sorry but that is incorrect since Gparted is not installed by default but can be installed from synaptic.

But you eeded to install ntfsprogs.

Code:

sudo apt-get install ntfsprogs

from this thread [http://ubuntuforums.org/showthread.php?p=2828520](http://ubuntuforums.org/showthread.php?p=2828520)

---

### Post by bren on 2007-06-18
> **era86 said:**
> i do so, but the ntfs option isnt allowed?  do i need any other programs or ibraries for this to work?

```
> sudo apt-get install gparted
```

or use gparted LIVE CD (to work on the partition you are booted from in future)

bren

---

