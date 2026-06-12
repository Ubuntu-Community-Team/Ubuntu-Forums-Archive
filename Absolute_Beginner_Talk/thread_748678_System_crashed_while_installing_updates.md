---
title: "System crashed while installing updates"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-04-07
And I had to hard reset my computer midway installing the updates. Now I have a "new updates available" notification icon and when i try to install the updates it gives this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I went into terminal, and ran what it said and this happens:

harrison@machine:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
harrison@machine:~$ 

??????

---

### Post by JoshuaRL on 2008-04-07
Try:
```

sudo dpkg --configure -a

```

Sudo means "super user do" and give you short-term root access (superuser privilege).

---

### Post by h-town on 2008-04-07
ahhhhh i get it. thanks a bunch!

---

