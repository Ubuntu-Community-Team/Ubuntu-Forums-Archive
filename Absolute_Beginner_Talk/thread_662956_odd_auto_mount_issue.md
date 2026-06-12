---
title: "odd auto mount issue"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by ARhere on 2008-01-09
Hello All,

Encountered an odd issue when trying to get fstab to automatically mount my USB hard drive on boot.

My fstab entry
```
/dev/sdc1	/home/andrew/Documents	ntfs-3g	rw,user,auto,exec	0 0
```

When I boot the machine, it boots not mounted and I still have to manually mount it.

I have tested my fstab using...
```
sudo mount -a
```
...and it mounts fine.

The reason I am not letting ntfs-3g automount it, is I want the mount point to be in my /home directory and not the /media directory.

Any ideas?  Is there a command that allows me to read mounting error messages from boot?

-AR

---

### Post by ARhere on 2008-01-10
Anyone have a clue?

-AR

---

