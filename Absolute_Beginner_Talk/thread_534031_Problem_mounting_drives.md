---
title: "Problem mounting drives"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by fredley on 2007-08-24
I'm mouting two usb drives, fat filesystem (I would change, but I don't have enough spare space to put everything while I reformat the drives). Their entries in fstab look like:

```
/dev/sda1       /mnt/320        vfat    iocharset=utf8,umask=000        0      0
/dev/sdb1       /mnt/160        vfat    iocharset=utf8,umask=000        0      0
```

I've done mount -a, and root can read/write fine but other users can't. Can someone help me out?

---

### Post by jamvegan on 2007-08-25
What are the permissions on your mount points?

---

### Post by Maxtorm on 2007-08-25
Try changing those umask entries to umask=0777.  Alternately, I believe you can specify uid and/or gid on each line of the fstab to give persmission to a specific user or group.  (To determine your current uid, use ```
id
```).

---

### Post by fredley on 2007-08-25
/

---

### Post by fredley on 2007-08-25
Ok after much fiddling, fstab looks like:
```

/dev/sdc1       /mnt/320        vfat    rw,exec,uid=1008,gid=1008,umask=0777    0       0
/dev/sdd1       /mnt/160        vfat    rw,exec,uid=1008,gid=1008,umask=0777    0       0
```

And it's all mounted up nicely.

But when I'm user 1008 I can't read let alone write.

---

