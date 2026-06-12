---
title: "live cd read only(how do i copy through the live cd?)"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by johnlee on 2007-07-07
i need to move some crucial files about on my ntfs formatted xp partition, the live cd says its read only
how do i change that?

---

### Post by Vajra Vrtti on 2007-07-07
By default, Ubuntu has only NTFS read support installed. You can try to install the package **ntfs-config**. Then you will find it in *System Tools*. If a reboot is not required (the installation will be lost in that case, if you are using the Live CD) you will be able to enable the read/write access with it.

---

### Post by kerry_s on 2007-07-07
it requires a special program  to write to ntfs, even then you still might corrupt it.

---

### Post by johnlee on 2007-07-07
a google and i stumbled upon this, however apt get says it cant find ntfs-config

---

### Post by Vajra Vrtti on 2007-07-07
*System >- Administration -> Software Sources*.
Enable the **universe** repository.

---

### Post by ghost_ryder35 on 2007-07-07
> **Vajra Vrtti said:**
> *System >- Administration -> Software Sources*.
Enable the **universe** repository.

+1

---

### Post by ugm6hr on 2007-07-07
> **johnlee said:**
> i need to move some crucial files about on my ntfs formatted xp partition, the live cd says its read only
how do i change that?
Surely it would be a lot faster to move those files from within XP?  Or at least from a Ubuntu installation (with ntfs-3g / ntfs-config)?

Any reason why you are using the LiveCD to do this?

---

### Post by johnlee on 2007-07-07
xp died ;( well, i got them off, and now reloading
thanks guyes

---

### Post by KuroRai on 2007-07-08
well if you are only moving, then you should be able to copy files fine off your HD, tis pasting thats the problem, iSuggest moving them onto an external drive formatted to FAT32...

and also, if you've figured it out yuo should change this thread to soloved (under tread tools at the top if you don't know how)!

---

