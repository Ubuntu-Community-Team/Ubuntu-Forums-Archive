---
title: "Renaming Drives"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by iancvt55 on 2008-02-16
Hi

I click on Places then Computer and I can see my drives. The linux one is named Filesystem.

How do I rename it?

Thanks

Ian

---

### Post by drs305 on 2008-02-16
My names are established in fstab. For instance:
# hda3
UUID=ed4d4989-b6ff-41fe-9c4d-c2378c201d34	/media/backup.images 		ext3 	defaults,user 	0 

shows up as "backup.images"

If you edit fstab, make a backup copy first!
```
sudo cp /etc/fstab /etc/fstab.bak
```

---

### Post by iancvt55 on 2008-02-16
DRS305...thanks will take a .bak first then see what happens

---

