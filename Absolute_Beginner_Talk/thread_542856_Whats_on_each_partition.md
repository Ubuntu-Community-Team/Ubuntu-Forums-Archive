---
title: "Whats on each partition"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by mar225 on 2007-09-04
Can someone tell me how to identify which directories are on which partition. I have searched and come up with about everything else.  

Thanks

---

### Post by newlinux on 2007-09-04
```

df -h 

```

will give you a list of mounted partitions and their mount points. That may help.

---

### Post by snowjm on 2007-09-04
EDIT: beat to the punch. =p

---

### Post by mar225 on 2007-09-04
Let me try again.   I know where the partitions are but how do you tell what directories are on which partition?   Example: which partition contains /home?

Thanks

---

### Post by newlinux on 2007-09-04
You can determine that by looking at the mount points of the partitions. For instance, if there isn't a partition mounted as /home then /home is on the root partition (the partition mounted as /).

---

### Post by mar225 on 2007-09-04
Thanx.  That gives me a place to start.

---

### Post by newlinux on 2007-09-04
Your welcome. There may be a more direct way, but I'm at an XP box and it I can't quite think of one of the top of my head... If I think of it I'll post back.

---

### Post by vanadium on 2007-09-04
The "df" is probably the most direct way. In principle, only the root (sysadmin) should worry about partitions. For the user, there is one streamlined directory tree that starts with / (root). The data of the user are, if all is well organised, accessible under the user's home directory: /home/$USER (where user is your login) or hortcut: ~ Exception: removable media in Ubuntu are mounted under /media and appear as an icon on the desktop.

---

