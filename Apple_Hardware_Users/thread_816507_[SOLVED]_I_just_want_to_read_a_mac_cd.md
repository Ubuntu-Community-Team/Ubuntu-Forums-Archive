---
title: "[SOLVED] I just want to read a mac cd"
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by skelooth on 2008-06-02
Hello, I just want to read some mac CDs on ubuntu. The newer ones work, but the CDs from a few years ago come up with an error:

```

Can not mount volume

Invalid mount option when attempting to mount the volume 'DBA_102'.
```

Is there anyway to read these CDs? And by any, I mean literally ANY way?

---

### Post by skelooth on 2008-06-02
Solved! 

I just had to manually mount it

mount -t hfs /dev/hdd /media/cdrom0

I don't know why automounter can't figure out it's hfs.

---

