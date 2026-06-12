---
title: "HD to share between windows and ubuntu?"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by Grahamb on 2006-04-01
What format does a Hard Drive need to be for it to be able to be seen by Windows (XP) and Ubuntu?

Thanks

---

### Post by taurus on 2006-04-01
Always fat32 (or vfat)...

---

### Post by Omnios on 2006-04-01
Personaly I have 50gigs as vfat32 formated in Linux from the terminal. Vfat kind of fakes permitions and works pretty well. Also xp will not format over 39gigs. Also not from what I read if you format it with Ubuntu from the terminal you can specify vfat-32 otherwise you might end up with fat16 but do not quote me on that as that is how I read it from the man page.

---

### Post by taurus on 2006-04-01
You can mount it as fat32 from /etc/fstab!  Just use "vfat" as filesystem...  :rolleyes:

---

