---
title: "How do you restore fstab from backup"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-08-03
I used   sudo   cp /etc/fstab   /etc/fstab.backup    To back up my fstab then proceeded to do some work which eventually messed up the fstab, how should you use the backup to restore the file, I was lucky I had posted mine in a thread and only had to copy and paste from there but there must be a proper way of doing it.
Thanks.

Mick

---

### Post by Rocket2DMn on 2007-08-03
just reverse the copy command
```
sudo cp /etc/fstab.backup /etc/fstab
```
This will overwrite your messed up fstab with your backup one.

---

### Post by omns on 2007-08-03
sudo cp /etc/fstab.backup /etc/fstab

---

### Post by MickS on 2007-08-03
Thanks I knew there would be a simple way when you know how.

Mick

---

