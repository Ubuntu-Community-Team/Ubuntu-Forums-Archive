---
title: "Making a drive acessable by Ubuntu and Windows"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Ophidian on 2006-10-21
Didn't install on Dimension 2350, but I did have success with installing on my notebook. Everything is going nicely, but I'm stumped with something. 

I have only one hard drive; however, it is partitioned. I placed the operating systems and applications on smaller partitions (about 20GBs each), then I have two other partitions--one which is about 30GB with some files, and an empty one which is about 20GB. 

The 30GB and 20GB partitions which are not for OS are in NTFS file system; but it would not be a challenge to change the 20GB file format.

I'd like to make one of these partitions accessible to both OS's; so I can get to various media files like music and images. Is it possible? What steps do I need to take?

---

### Post by raul_ on 2006-10-21
That shouldn't be a problem. For example, both Windows and Linux recognize usb Pen drives. I think that a partition with the same file system would be recognized by both. I think pen drives use fat32 but i'm not sure. Maybe some1 more experienced can answer your question better but i think what i said is correct

---

### Post by lreyes6 on 2006-10-21
yeap it is fat32.... it's fully supported in Gnu/Linux for read-write unlike ntfs that is only supporting for reading (and under root)

---

### Post by argie on 2006-10-21
You could also format it ext2 and then use the ext2 file system driver from here:
[http://fs-driver.org/](http://fs-driver.org/)

---

### Post by jordanmthomas on 2006-10-21
fs-driver also works with ext3

---

