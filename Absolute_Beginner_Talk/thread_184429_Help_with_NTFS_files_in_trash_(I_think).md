---
title: "Help with NTFS files in trash (I think)"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Denim on 2006-05-29
I have 2 days of experience with Ubuntu, and I know I will stick with it. I managed to send a couple files to the trash that I can't delete. I have a NTFS partition that I added to the desktop. Along the way (not sure when), I sent Recycler and System Volume Information folders to the trash. I thought these were XP folders and I wouldn't need them anymore. Now I can't get rid of them due to permissions. Is there any hope? ](*,) 

Any info appreciated.

---

### Post by aysiu on 2006-05-29
Try pasting this command into the terminal: ```
sudo rm -rf ~/.Trash/*
```

---

### Post by Denim on 2006-05-29
That was too easy. Thanks!
I obviously have a bit of reading to do.

---

