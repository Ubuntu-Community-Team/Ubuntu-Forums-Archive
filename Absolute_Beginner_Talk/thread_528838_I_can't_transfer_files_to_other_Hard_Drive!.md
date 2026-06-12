---
title: "I can't transfer files to other Hard Drive!"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by black_mag on 2007-08-18
I am trying to transfer files to my other hard drive but I get this error:

Error while copying to "/media/disk/Documents and Settings."
You do not have permissions to write to this folder.

How do I fix that?

---

### Post by overdrank on 2007-08-18
> **black_mag said:**
> I am trying to transfer files to my other hard drive but I get this error:

Error while copying to "/media/disk/Documents and Settings."
You do not have permissions to write to this folder.

How do I fix that?

Hi and well two things, is the drive mounted and is it ntfs. If yes to both you will need to mount the drive then you will need to install ntfs-config and ntfs-3g. You can install these via synaptic manager and search for ntfs and you will find them. Good luck

---

### Post by taurus on 2007-08-18
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by overdrank on 2007-08-18
> **taurus said:**
> [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Even Better :guitar:

---

### Post by black_mag on 2007-08-18
I still cant transfer and iI get the same error.

---

### Post by taurus on 2007-08-18
Post

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by black_mag on 2007-08-18
same error

---

