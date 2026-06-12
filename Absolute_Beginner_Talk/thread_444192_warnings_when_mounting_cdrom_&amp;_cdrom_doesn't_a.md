---
title: "warnings when mounting cdrom &amp; cdrom doesn't auto mount"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by daveblack on 2007-05-15
Hi

My cdrom stoped mounting automatically after I changed the cdrom mount codepage in fstab (so I could view other languages' filesystems). When I mount it manually, it mounts, but this is what I get:

```
dave@xxxx:~$  sudo mount -a
mount: block device /dev/scd0 is write-protected, mounting read-only
```

This is my fstab:

```
dave@xxxx:~$ cat /etc/fstab | grep scd0
/dev/scd0 /media/cdrom0 udf,iso9660 defaults,iocharset=utf8 0 0
```

What could be the problem?

Thanks
Dave

---

### Post by klytu on 2007-05-15
> **daveblack said:**
> Hi

My cdrom stoped mounting automatically after I changed the cdrom mount codepage in fstab (so I could view other languages' filesystems). When I mount it manually, it mounts, but this is what I get:

```
dave@xxxx:~$  sudo mount -a
mount: block device /dev/scd0 is write-protected, mounting read-only
```

This is my fstab:

```
dave@xxxx:~$ cat /etc/fstab | grep scd0
/dev/scd0 /media/cdrom0 udf,iso9660 defaults,iocharset=utf8 0 0
```

What could be the problem?

Thanks
Dave

Try changing that fstab line to: > /dev/scd0 /media/cdrom0 udf,iso9660 **user,noauto**,iocharset=utf8 0 0

EDIT: Corrected the above line. This should work. I think the defaults option is what is giving you trouble. See ```
man mount
```for what this does in detail

---

### Post by daveblack on 2007-05-16
thanks, klytu. Now it works great. It also worked with your other version (- before the edit), but I had to remove the auto. Like this:
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,defaults,iocharset=utf8 0 0
```

---

