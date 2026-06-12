---
title: "Why can't I write to an external hard drive"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by secallen on 2006-08-22
Hi,

I'm running dapper Drake and can read an external USB hard drive but when I try to write to it it says the drive is not mounted. What am I doing wrong?

Thanks

---

### Post by Major_Stitch on 2006-08-22
Did you really mount it?
Check this: [Mount]("https://help.ubuntu.com/community/Mount")

---

### Post by secallen on 2006-08-22
No, I didn't do anything to the drive other than plug it into the computer. Do I have to "mont" it every time I plug it in?

---

### Post by secallen on 2006-08-22
Sorry, "mount" it..

---

### Post by Arkian on 2006-08-22
You have to format the drive. Depending on how you will use it, you should put an ext or FAT32 filesystem on it.

EDIT:

Sry didnt read your first post thoroughly enough. If you've already put a FAT32 on the drive, then no need to do it again. Must be some kind of mounting issue then.

---

### Post by secallen on 2006-08-22
Hi,

the drive is already formatted as fat32 and I can read/write to it in Windows. In Ubuntu I can only read. Do I still have to reformat it?

---

### Post by jethro10 on 2006-08-22
I installed Gparted from the repositories and then was able to format it as ext3.

The next time i used it was after a re-boot amd it just discovered it like a really big memory stick!

J

---

