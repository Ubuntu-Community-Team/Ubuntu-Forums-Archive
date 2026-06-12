---
title: "Access right to EXT3 partition"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Hillerd on 2007-01-24
Here comes an absolute beginner question:
I created a new partition, this is how it is mounted in fstab:
```
/dev/hda10      /wine ext3 defaults 0 2
```
and these are the access rights I get:
```
drwxr-xr-x   5 root root     4096 2007-01-24 21:43 wine
```
You see, no write access for others.
So when I am running as ordinary user (as always) I cannot write to files on that partition. How can I change that?
I tried to add ```
umask=000,
``` to fstab, but then mount does not want do mount it anymore, probably because this option is only available for FAT.

Thanks
 Dietmar

---

### Post by Bachstelze on 2007-01-24
ext3 handles individual file permissions so you don,'t need to use umask at mount time. Just mount it with defaults and use chown/chmod to set ownership/permissions as you wish.

---

### Post by taurus on 2007-01-24
I will assume your login name is **hillerd** so change it to whatever it actually is.

```
sudo chown -R **hillerd**:**hillerd** /wine
```

---

