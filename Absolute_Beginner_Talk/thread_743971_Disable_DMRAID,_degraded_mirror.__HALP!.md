---
title: "Disable DMRAID, degraded mirror.  HALP!"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by adelodder on 2008-04-03
I have 4 SATA drives.

SATA1 and SATA2 form a RAID0. all works fine here. But,

**SATA3 and SATA4 are 2 independent drives that DMRAID wrongly considers as a RAID1 setup.**
```
ERROR: creating degraded mirror mapping for "sil_aebidgcfdhbb"
```

Impossible to access 1 of the drives.
```
**Cannot mount volume.**
You are not privileged to mount the volume 'Downloads'.
```

Workaround:
```

sudo dmraid -an
sudo mount -a

```

**Can I configure DMRAID so it won't consider SATA3 and SATA4 to be part of a RAID?**

---

