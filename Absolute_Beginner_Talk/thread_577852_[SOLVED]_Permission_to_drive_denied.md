---
title: "[SOLVED] Permission to drive denied"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-16
I have a dual boot machine with several partitions. I recently used Acronis Disk Director in Windows to convert a small FAT32 drive to ext3. When in Ubuntu, I can see the drive and copy and open material from it. However I cannot put anything on it. I get the permission denied error on it. It is owned by ROOT.

How can I change the permissions so I have full access from this file under Linux?

---

### Post by bsharp on 2007-10-16
Open a terminal and 
```
sudo chown *yourusername* /whereveritismounted
```

---

### Post by Alan Stancliff on 2007-10-16
> **bsharp said:**
> Open a terminal and 
```
sudo chown *yourusername* /whereveritismounted
```

That did it. Thanks

---

