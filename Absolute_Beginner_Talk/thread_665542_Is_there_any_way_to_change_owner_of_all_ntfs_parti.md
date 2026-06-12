---
title: "Is there any way to change owner of all ntfs partition to be myself?"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-12
Thank you for reading my post
Is there any way to change owner of all ntfs partition to be myself?
whenever i want to do something with ntfs partitions it asks return error that I have no permission.
Thanks.

---

### Post by taurus on 2008-01-12
Instead of mounting it with ntfs driver, why not mount with ntfs-3g driver so you can write to it anytime you want.  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```
p.s.  Which release are you running right now?

---

