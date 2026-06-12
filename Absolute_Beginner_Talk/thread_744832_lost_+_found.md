---
title: "lost + found"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by stoppage on 2008-04-04
Something really odd in my "Feisty"......I don't have a "lost + found" folder! Anybody?

---

### Post by The Titan on 2008-04-04
i don't know why it isn't there, i have it in 8.04. what is the "lost + found" folder for anyways.

---

### Post by PointyWombat on 2008-04-04
The lost+found directory should be at the root of every file system. You can create it with the mklost+found command:

```
cd /
sudo mklost+found
```

It is possible to delete this directory with elevated privileges, so perhaps that's what happened in your case.

The lost+found directory is used to store files recovered through fsck if the file system gets corrupted. The recovered files would be named by the inode from which they were recovered from.

---

### Post by mcduck on 2008-04-04
Usually fsck should just automatically create the lost+found directory if it doesn't exist and fsck needs it. So you shouldn't worry if the directory isn't there.

But if you want to create the directory yourself, you should use the "mklost+found"-command.

---

