---
title: "FAT32 compatibility test utility?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-06-22
I've got the not-unusual setup of one drive in ext, and the other drive in FAT32. Great, but you can do things on the ext like have files Foo.jpg and foo.jpg coexist, but not on FAT32. That's a problem when I want to move a bunch of directories from ext to the simpler FAT32. 

So is there a utility I can run on ext directories to tell me what's in there that has to be changed before going to FAT32?

While I'm asking about utilities that the Linux-savvy would know of, how about a checksum comparator? The one in GQview is excellent and exactly what I want, except it only does images. What's the way for all files?

Thanks.

---

### Post by DBStevens on 2007-06-23
For a checksum utility take a look at md5

man md5  should provide some information.

---

