---
title: "[SOLVED] truecrypt filesystem"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by skippy_1 on 2008-02-07
I created a volume and am trying to mount it but it keeps saying "mount: you must specify the filesystem type", I tried looking through it's options and almost *everything* on the internet but I can't figure it out...it's fat. How do I get it to load?

---

### Post by superjacent on 2008-02-07
The thread is marked as SOLVED.   How did you resolve it?

---

### Post by peterdk on 2008-05-18
I guess he used something like ```
mount **-t vfat** [..] 
```

---

### Post by sparrowkc on 2008-06-15
Some info that might help people who find this thread,  for an unformatted truecrypt volume, find out what to give mkfs.ext3 with truecrypt -l

---

