---
title: "Accessing USB Hard Drive"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-04-23
For some reason I can see my USB hard drive and the files on it, but can't write to it.  Ubuntu says I don't have permission to it.  How can I unlock it?

---

### Post by Qrk on 2006-04-23
edit /etc/fstab

```
gksudo gedit /etc/fstab
```

Find the line corresponding to your USB hard drive, (if you don't know, you can type fdisk -l into a terminal) [B]Make sure that it is not formated with ntfs. 
[/B]
Change the third column to read "defaults" which will automatically mount it at boot and allow you to read an write to it.

Now do```
sudo mount -a
```

---

