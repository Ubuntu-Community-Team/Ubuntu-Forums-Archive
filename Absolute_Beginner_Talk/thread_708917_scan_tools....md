---
title: "scan tools...?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by niko123 on 2008-02-26
hi guys...i wanted to know if there are any scan tools...to check the whole ubuntu...because i just had a "Duplicate or bad block in use" and i wanted to make sure there is nothing else wrong...?

can anyone provide me a scan tool...or any ideas

---

### Post by Paqman on 2008-02-26
You want to scan your drive for errors? You can boot into a LiveCD and run [fsck](http://en.wikipedia.org/wiki/Fsck) (LiveCD because you should never run fsck on a mounted file system)

---

### Post by nick_h on 2008-02-27
You can also use the badblocks command to check a device for bad blocks.

To read the manual page type:
```
man badblocks
```

---

