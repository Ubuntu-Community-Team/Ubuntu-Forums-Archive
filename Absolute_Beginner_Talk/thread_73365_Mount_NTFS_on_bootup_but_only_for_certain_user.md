---
title: "Mount NTFS on bootup but only for certain user"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by daahli on 2005-10-08
Hey guys,

Hope somebody here can help me out. The following mounts my ntfs partition on bootup for all users:

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

How can I make it only mount for a certain user?

Thanks!

---

### Post by adwait on 2005-10-08
You can make it accessible only to a certain user. Just add
```
uid=<uid of user> 
```
the the umask.
You can find the UID of the user by logging in as him and using
```
echo $UID
```

---

