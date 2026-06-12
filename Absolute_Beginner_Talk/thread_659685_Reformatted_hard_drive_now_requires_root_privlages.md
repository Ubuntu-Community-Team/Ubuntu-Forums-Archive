---
title: "Reformatted hard drive now requires root privlages to access."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Surreal Killa on 2008-01-06
I formatted my external hard drive, which was NTFS, which worked perfectly (could read and write to it without needing to enter password) with GParted to ReiserFS and now whenever I try to write to it it makes me put my password in. Why? And how do I change it?

---

### Post by taurus on 2008-01-06
You need to change the ownership of the mount point of that drive from root to your login name if you want to write to it without root privilege.  _Assuming_ you've mounted it to /media/share and your login name is **surreal**, run

```
sudo chown -R **surreal**:**surreal** /media/share
ls -la /media
```

---

### Post by Surreal Killa on 2008-01-06
Thanks.

---

