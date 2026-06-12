---
title: "Programs seperate from OS"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by hfw on 2007-08-13
Can programs be kept/installed on a separate partition from my OS or do they need to reside in the same partition?

Thanks,
Hal

---

### Post by schorsch on 2007-08-13
It is possible to partition a disk so that /usr (where programs are normally installed), /var (log files), /tmp, / and all other directories are on a separate partitions .... and linux will still work afterwards.

---

### Post by hfw on 2007-08-13
that "and Linux will still work" part is important.  Thanks for the quick reply.

---

### Post by Hospadar on 2007-08-13
When you are installing, you could mout different partitions to /usr /var /temp etc (really /usr is where most of the data goes) and it would put anything you installed there to those partitions.

You could probably also do this post-install by editing you /etc/fstab and copying some files over ahead of time, but that seems rather risky and quite difficult.  I would only attempt this with a fresh install if it were me.

---

