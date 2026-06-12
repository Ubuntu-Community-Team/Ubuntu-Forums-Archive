---
title: "I mounted ntfs during install now how to make it writeable?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by alexlex on 2007-05-14
as the question reads how do i give my already mounted ntfs hd partitions write access?

---

### Post by bobplano on 2007-05-14
look for ntfs3g
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs3g)

---

### Post by ivanoz on 2007-05-17
i had ntfs3g installed in my dapper, now i have feisty and dont know if the same commands will work on that too, please tell me if its the same process or if something needs to be changed.

Cheers

---

### Post by mikewhatever on 2007-05-17
> **ivanoz said:**
> i had ntfs3g installed in my dapper, now i have feisty and dont know if the same commands will work on that too, please tell me if its the same process or if something needs to be changed.

Cheers

ntfs-3g is in the repositories in Feisty, so you do not need to add extra ones.

---

### Post by jiminycricket on 2007-05-17
I also recommend ntfs-config in the universe repository :)  Does a lot of the work for you (hail givre for the GUi, and the creators of ntfs-3g like Szabolcs...)

---

### Post by aysiu on 2007-05-17
This guide will help you:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by ivanoz on 2007-05-17
cheers, that was the info i needed, i forgot that the name was just ntfs-config and not ntfs3g-config.

cheers

---

