---
title: "how to copy a hard drive partition"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by ronlybonly on 2006-08-15
hello. i just bought a new hard drive, and i was wondering what would be the easiest way to copy over all of the data from a partition on my old hard drive. Would a simple ```
sudo cp /* /mnt/newpartition -R
``` do the trick?

---

### Post by h2gofast on 2006-08-16
```
sudo cp -a /  /mnt/newpartition
```

if you type "man cp" in the terminal it will give you the rundown on cp command.  

Some folks may suggest using the dd command.  I would advise against this based on advice from more experienced users.

---

### Post by BioTeX on 2006-09-02
I would suggest installing GPartEd and using that to copy and paste the partition. That way you guarantee no files are left out.

---

### Post by aysiu on 2006-09-02
I would suggest PartImage:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

