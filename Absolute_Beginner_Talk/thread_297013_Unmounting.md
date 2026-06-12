---
title: "Unmounting"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by dmce on 2006-11-10
Hi

I have searched but could not find much of an answer, so i hope its ok to ask. I have one ntfs drive mounted and i also occasionally mount a remote folder using SSH (my web site). My question is, do i have to umount before i shut the system off, or does a shutdown unmount?

David

---

### Post by taurus on 2006-11-10
Shutdown will unmount it but if you want to unmount it before you shutdown the computer, do it from a terminal.

```
sudo umount <mountpoint>
```

---

### Post by dmce on 2006-11-10
Thanks taurus. Didnt want to do any damage by not unmounting before shutting down.

---

