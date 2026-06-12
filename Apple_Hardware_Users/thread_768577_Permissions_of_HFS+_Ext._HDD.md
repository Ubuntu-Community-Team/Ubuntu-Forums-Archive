---
title: "Permissions of HFS+ Ext. HDD"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by arseniy on 2008-04-26
I have two HFS+ partitions on my external hard drive that contain all my documents, music, movies, photos, etc. Everything that's important and that I want on Ubuntu. The last time I tried to do it, here's what I did. I made a directory in /mnt and mounted the HFS+ drive (one of them) to that new directory. Then, using gknautilus opened by root, I was able to open folders in the HFS+ drive and copy them to Ubuntu. But I couldn't edit them or do anything. Is there a better/easier way to do it?

---

### Post by cyberdork33 on 2008-04-26
> **arseniy said:**
> I have two HFS+ partitions on my external hard drive that contain all my documents, music, movies, photos, etc. Everything that's important and that I want on Ubuntu. The last time I tried to do it, here's what I did. I made a directory in /mnt and mounted the HFS+ drive (one of them) to that new directory. Then, using gknautilus opened by root, I was able to open folders in the HFS+ drive and copy them to Ubuntu. But I couldn't edit them or do anything. Is there a better/easier way to do it?
you cannot write to a HFS+ drive with journaling turned on... and I wouldn't trust it when it is off personally.

in OSX terminal:
```
diskutil disableJournal volumeName
```

---

### Post by arseniy on 2008-04-26
Can I do that from the Ubuntu terminal? I don't have OS X installed, just Ubuntu. And here's an update:

I tried what I did that last time again, and now all I see under the Users/Arseniy folder is text files named Music, Movies, etc. instead of folders.

---

### Post by cyberdork33 on 2008-04-26
there is no way to do it without OSX that I know of. 

Why are you using HFS+ for your hard drives if you do not use OSX?

---

