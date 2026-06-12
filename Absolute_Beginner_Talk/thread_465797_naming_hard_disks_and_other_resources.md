---
title: "naming hard disks and other resources"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-06-06
Is it feasible to give resources, particularly hard disks and cd drives, aliases or alternative names which are human-friendlier than hda6 and so on? And if so, can these names subsequently be changed if need be?

---

### Post by viciouslime on 2007-06-06
You could just make symbolic links. :)

---

### Post by freebird54 on 2007-06-06
I just gave them 'human friendly' mount points  (like /media/data and /media/backup) but if you want friendlier previous post is correct...  :)

---

### Post by Skrynesaver on 2007-06-06
You can add labels to partitions (e2fslabel if i remember correctly) and then mount them using the label (mount -L "labelname" /mountpoint).  In fstab you can use LABEL=labelname as the partition id

---

