---
title: "unmounting harddrives"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-08-04
I recently installed ubuntu. During the installation it asked me whether i'd like to mount my other harddrive which was partition into 2 halves (hdb1 and hdb2). Today, i reformatted that harddrive and made it one partition( hdb). The problem is when i boot up ubuntu it does a system check or something and tells me it can no longer find the old paritions and asks me to fix it manually. In addition, my new harddrive (hdb) is no auto mounted on start up like the others were (which makes sense). Is there a way i can fix this so that my new hdd mounts automatically and the system check on start up no longer tells me i can't find them and to fix them manually?

Thanks,
cptjaben

---

### Post by jd65pl on 2006-08-04
try

```
sudo gedit /etc/fstab
```

This file contains those drives to mount automatically

---

