---
title: "Audacity - Saving to a different partition...."
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ElEdwards on 2007-06-07
I have a FAT32 partition on my laptop's hard drive so I can share files between Windows XP and Ubuntu (dual boot).

While in Ubuntu, I can see and use this partition in File Manager but when I try to save a file in Audacity, all I can access is my Ubuntu parition.  How do I access this other FAT32 partition in Audacity?

Thanks :)

---

### Post by Ek0nomik on 2007-06-07
> **ElEdwards said:**
> I have a FAT32 partition on my laptop's hard drive so I can share files between Windows XP and Ubuntu (dual boot).

While in Ubuntu, I can see and use this partition in File Manager but when I try to save a file in Audacity, all I can access is my Ubuntu parition.  How do I access this other FAT32 partition in Audacity?

Thanks :)

Are you sure you can't type in the path?

---

### Post by ajgreeny on 2007-06-07
That partition will need to be mounted as user writable, not root, which it will normally be if it's in /media.  You may need to chown on the folder.

---

