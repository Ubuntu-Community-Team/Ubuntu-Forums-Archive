---
title: "update error really don't know what to do"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by psyionx on 2008-01-14
hi there, can anyone help me what do i do with this...
i tried to update. the update manager will stop and give me this message.

```
E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.22-14-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko')
```

i did tried reboot then update but this still the same...

---

### Post by dstew on 2008-01-14
Try **sudo apt-get update** on the command line, then try to use the update manager and see if you get farther.

---

