---
title: "I can't mount devices from nautilus!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-12-11
If I try to mount any of my two partitions from nautilus, it tells me that "I have not permissions to do this". But, I can mount them with the command line (using mount). What can the problem be?

---

### Post by jken146 on 2007-12-11
You need to be root (use sudo) to mount/unmount most things.  Where this is not the case, the user who mounted a device must be the one who unmounts it.

(Not recommended for everyday use) You can run Nautilus in super user mode with ```
gksu nautilus
```

---

### Post by jken146 on 2007-12-11
You can also edit the file /etc/fstab to make partitions mount automatically (you need to create a folder for each of them first (usual places are in /media and /mnt).

---

