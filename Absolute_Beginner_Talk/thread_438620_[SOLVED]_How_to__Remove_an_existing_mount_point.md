---
title: "[SOLVED] How to : Remove an existing mount point ?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-09
How do I remove an existing mount point for an external drive ?

---

### Post by drowner on 2007-05-09
Do you want to unmount the drive?

Or mount it somewhere else?

---

### Post by Inxsible on 2007-05-09
mount it somewhere else

---

### Post by drowner on 2007-05-09
did you mount it yourself? or did it happen automatically?

---

### Post by Inxsible on 2007-05-09
I created the mount point myself 


when I try to unmount it it gives me an error
```

Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

```

---

### Post by drowner on 2007-05-10
Well, I'm lost.

Maybe someone else can jump in.

But first, if I knew th answer, i *think* i would want to know what your mtab says.

And, possibly your fstab too. I dont know if it helps, but it cant hurt knowing.

---

### Post by Inxsible on 2007-05-10
i was trying a bunch of things...

what finally worked...was I disconnected the drive and then also removed its entry from mtab. Then simply did a ```

rm -R /<MOUNT_POINT>

```

and that got rid of the folders...When i re-connected my drive again, I simply mounted it again to a new location.

---

