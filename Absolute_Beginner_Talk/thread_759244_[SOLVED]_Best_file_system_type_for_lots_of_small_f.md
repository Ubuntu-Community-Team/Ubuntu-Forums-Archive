---
title: "[SOLVED] Best file system type for lots of small files"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-18
Hiya, I have a lot of music thats all in folders on a external HD(top quality) and it takes quite a while ot load directories(nautilus) so i can see what files are on it.

1.) whats the best file system for lots of small file.
2.)well i benefit (load time) by splitting them songs into folders (Artist/Albulm)

Saj

---

### Post by Bachstelze on 2008-04-18
When speaking of filesystems, "small files" means *really* small files (i.e. under 1 KB). I think XFS or JFS would be the best choices for you. What is the drive formatted in, currently ?

---

### Post by saj0577 on 2008-04-18
Ext3 and ntfs putting two collections together.

So xfs for lots of songs?

---

### Post by Bachstelze on 2008-04-18
Yep, or JFS (sorry for the typo). XFS usually performs a bit better than JFS and has been around for longer, but it is more RAM-intensive, and thus is also very vulnerable to crashes (i.e. if your system crashes, you might lose quite a bit of data which will be still in RAM and not actually written to the disk yes).

---

### Post by saj0577 on 2008-04-18
Thanks
Format as xfs in gparted im guessing yeah?

Saj

---

### Post by Bachstelze on 2008-04-18
Yep, or use *mkfs.xfs* from the CLI if you're feeling geeky ;)

---

### Post by saj0577 on 2008-04-18
Feeling geeky that sounds like my way of doing it.

Thanks alot
Saj

---

### Post by Bachstelze on 2008-04-18
By the way, as I said earlier, XFS intensively caches data in RAM to enhance performance, and data is sometimes actually written on the disk **several hours** after you perform your write operation on the filesystem. Therefore, you should **always** make sure your filesystem has been properly unmounted (which forces all data remaining in cache to be written on the disk) before unplugging the drive, or you could lose quite a bit of data.

---

### Post by Can+~ on 2008-04-18
XFS is supposedly a fast file system, on the other hand, Ext3 is known as a stable one.

Arstechnica has an extensive review and history for each kind of filesystem:
[http://arstechnica.com/articles/paedia/past-present-future-file-systems.ars](http://arstechnica.com/articles/paedia/past-present-future-file-systems.ars)

---

