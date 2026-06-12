---
title: "Can i view my ubuntu partition in vista?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by PharaohSD on 2007-09-24
Hi everyone,

installed Ubuntu Ultimate, and mounted my windows file system there,

but now i want to mount my ubuntu partition in vista, (to access all my files)

but i can't....

i think i need ext2 read/write capability in windows, what's the best solution?


thanks

---

### Post by LaRoza on 2007-09-24
The best solution is to make a separate partition for sharing data.

---

### Post by master_kernel on 2007-09-24
> **LaRoza said:**
> The best solution is to make a separate partition for sharing data.
LaRoza is right. Microsoft is so evil, they only want you to use their software, so they do not supply recognition software for ext* in Vista.

---

### Post by Maxtorm on 2007-09-24
I do this regularly, but under Windows XP, using the Ext2 IFS driver for Windows (see: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)). I quickly checked the site and didn't see any reference to Vista support, so your mileage may vary.

---

### Post by LaRoza on 2007-09-24
> **master_kernel said:**
> LaRoza is right. Microsoft is so evil, they only want you to use their software, so they do not supply recognition software for ext* in Vista.

...and they make NTFS difficult to play with.

Vista changed NTFS, so old tools do not work with it very well, it can make Vista unbootable, which is not a bad thing in my book, but you don't want that probably.

Use a new partition, in FAT32 if you are not storing files larger than 4 GB.

---

### Post by Maxtorm on 2007-09-24
Actually, according to this post [http://ubuntuforums.org/showthread.php?t=358241](http://ubuntuforums.org/showthread.php?t=358241) it would seem you can get ext2 support working under Vista without breaking anything else.

---

### Post by LaRoza on 2007-09-24
> **Maxtorm said:**
> Actually, according to this post [http://ubuntuforums.org/showthread.php?t=358241](http://ubuntuforums.org/showthread.php?t=358241) it would seem you can get ext2 support working under Vista without breaking anything else.

That would not be a good decision. Giving Windows write access to you Ubuntu partition is asking for trouble.

Actually, giving Vista write access to anything wouldn't be a good idea.

---

