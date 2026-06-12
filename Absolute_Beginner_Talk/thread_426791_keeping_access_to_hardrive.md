---
title: "keeping access to hardrive?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-04-28
so how do i keep a hard -drive mounted?

---

### Post by raja on 2007-04-28
Not clear what your question is.

For a hard drive to be mounted each time during booting, there must be a corresponding entry in /etc/fstab. If that was what you are asking about.

---

### Post by thelegionnaire on 2007-04-28
for example, if i want my desktop pic to be from my windows c drive, how would i do that?

---

### Post by raja on 2007-04-28
If you dual boot with Ubuntu, you can still access the NTFS drives in windows. If you want read-access only, it is there - out of the box.

---

### Post by thelegionnaire on 2007-04-29
but i have to mount it each boot

---

### Post by raja on 2007-04-29
No. It will be automatically detected and mounted.

---

### Post by thelegionnaire on 2007-05-01
how would i add the entry in fstab?

---

### Post by raja on 2007-05-01
Have you already installed Ubuntu as a dual boot or are you thinking of it? Usually the NTFS drives are detected and mounted automatically. If you have installed Ubuntu and the NTFS partitions are not showing up, only then you have to add the entries manually.

---

