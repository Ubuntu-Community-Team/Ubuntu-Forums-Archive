---
title: "Testing my Raid5"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-11-14
Hi All,

I want to test my RAID.. however, i want to completely fill the raid then remove a disk.

Is there a commands or something i can uses to create a file to fill the raid? I.E create a 600GB Text File????

Any help would be great.

Kind Regards

Robin

---

### Post by kidders on 2007-11-15
Hi there,

If you really want to create a 600GiB file, I suppose you could try something like ...```
dd bs=4096 count=150M if=/dev/urandom of=/path/to/file
```

Obviously, it would take quite some time, and be sort of pointless, but provided you're writing to a filesystem that supports 600GiB files, it should do the trick.

---

