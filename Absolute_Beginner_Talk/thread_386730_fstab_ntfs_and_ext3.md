---
title: "fstab ntfs and ext3"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by XotiC on 2007-03-17
Swedish letters "åäö" doesnt work on the ext3 but it works on the ntfs.

Here is my output for the ntfs and ext3:
```

/dev/hdb5 /mnt/hdb5 ext3 defaults 0 0
/dev/hdb6 /mnt/hdb6 ntfs-3g locale=sv_SE.utf8 0 0

```

I know that there is that "locale=sv_SE.utf8" to the ntfs and it is probably why it works. But i want to know how to put it on the ext3? do i have to remove the defaults?

---

