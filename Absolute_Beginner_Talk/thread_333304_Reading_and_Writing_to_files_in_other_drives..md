---
title: "Reading and Writing to files in other drives."
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Ahmed Fathy on 2007-01-07
I'm a totally newbie , i just installed Ubuntu Edgy three days ago and my problem is:

I have other two hard drives that i cant access..i read tens of  tutorials and i couldnt do anything with them !!

drives are hda1, hda2

they are NTFS drives

I really need help :(

---

### Post by nite owl on 2007-01-07
By cant access do you mean that you cant see them??? Or isn't it letting you access files on those drives???saying something like permision denied or similar??

---

### Post by meng on 2007-01-07
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

This will give you read-only access. If you need to have read-write access, you'll need to use ntfs-3g rather than ntfs, the former is considered a bit experimental. There is a howto on nfts-3g, you can search the forums for it.

---

### Post by PPAAUULL on 2007-01-07
I wouldn't recomend being able to Read-Write to the NTFS drive seeing as I have heard that you can run into some problems but if you really want to write to the NTFS drives that is about the only way to go.

---

