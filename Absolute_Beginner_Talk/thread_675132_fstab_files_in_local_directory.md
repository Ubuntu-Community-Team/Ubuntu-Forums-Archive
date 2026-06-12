---
title: "fstab files in local directory"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-01-22
Is there any mouting commands such as what is in /etc/fstab stored in your home directory that takes priority over the /etc/fstab one?

---

### Post by meborc on 2008-01-22
> **noorez said:**
> Is there any mouting commands such as what is in /etc/fstab stored in your home directory that takes priority over the /etc/fstab one?

no, the fstab file from /etc/ is used while booting/loading the OS... for security reasons it would be a very bad-bad-bad :) idea to let the system use a file from the users home dir

---

### Post by rosegarden78 on 2008-01-22
USB Drives:
mount /dev/sda# /mnt/yourMountFolderHere
mount /dev/sdb# /mnt/yourMountFolderHere

Just look for Johnny-Come-Lately in /etc/fstab and /etc/mtab when you plug in your device or don't know the number.  There are also special ways to mount files and disk images but that's another story.

---

