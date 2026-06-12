---
title: "Mounted folder is gone after reboot"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Miandrital on 2006-11-28
Hey all, after running the following code:

```
sudo mount --bind /shared /home/username/Desktop/shared
```

I get the shared folder mounted on my desktop, but whenever I reboot the desktop folder is just a blank folder.  Is there anything I can do to make this stay mounted after a reboot?



Thanks.

---

### Post by Bachstelze on 2006-11-28
No need for a bind here, just create a symlink :

```
ln -s /shared ~/Desktop
```

---

### Post by Miandrital on 2006-11-28
Awesome, many thanks!

---

