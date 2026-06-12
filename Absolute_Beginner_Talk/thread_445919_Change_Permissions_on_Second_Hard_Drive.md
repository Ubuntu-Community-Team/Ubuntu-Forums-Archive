---
title: "Change Permissions on Second Hard Drive"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by locustfist on 2007-05-16
My second hard drive is 'read only'. How do I change that? Does it involve wiping it?

---

### Post by taurus on 2007-05-16
What filesystem is that second harddrive?

```
sudo fdisk -l
```

---

### Post by locustfist on 2007-05-16
ntfs

---

### Post by taurus on 2007-05-16
And I assume you are running Feisty.

```

sudo aptitude update
sudo aptitude install ntfs-3g ntfs-config
gksudo ntfs-config
```
And point it to your second harddrive, ntfs partition.

---

### Post by locustfist on 2007-05-16
does this wipe the drive? Should i back it up? i generally back it up weekly.

---

### Post by taurus on 2007-05-16
It should not wipe your second harddrive.  It will configure and mount your second harddrive with ntfs-3g driver so you can write to it.

But backin up your important data before you do anything to it is always a good idea.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

