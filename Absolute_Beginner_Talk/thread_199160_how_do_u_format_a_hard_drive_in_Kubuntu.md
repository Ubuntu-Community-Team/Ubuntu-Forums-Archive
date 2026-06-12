---
title: "how do u format a hard drive in Kubuntu?"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-18
I installed another hard disk in my kubuntu box it was used for xp so it's ntfs kde wants to mount it as ntfs i want to format it to ext3 then mount the drive..I can't find an option to format that drive

---

### Post by aysiu on 2006-06-18
```
sudo aptitude update
sudo aptitude install gparted ntfsprogs
kdesu gparted
```

---

