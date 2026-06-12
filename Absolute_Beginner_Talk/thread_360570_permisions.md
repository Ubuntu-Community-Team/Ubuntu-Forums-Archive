---
title: "permisions"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by celticbhoy on 2007-02-13
I have set up a dual boot system with xp. I want to save a file to one of my shared drives but ubuntu tells me I dont have permision to write to the drive. how do i fix this

---

### Post by jvc26 on 2007-02-13
Thats probably because your XP drive is formatted in NTFS which is a Microsoft proprietary FS. You may want to check out [ntfs-3g]("http://www.ntfs-3g.org/") which I seem to remember being the drivers you need to get read-write permissions. Search the forums for more info as I'm sure there is a HOWTO about it somewhere.
Il

---

### Post by highneko on 2007-02-13
Do you know the filesystem the drive uses? Pasting some commands might help. I think these might be useful:
```
sudo fdisk -l
df -h
ls -l /media
mount
```

---

