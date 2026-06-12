---
title: "[SOLVED] Changing permissions"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-06-29
How can I change permission on 2 partitions. At the moment root has permission but I don't.

There are so many threads here that I can't work out what I should be doing.
Tried simple stuff like running nautilus as sudo - but it won't let me change permissions.

I can copy files in and out and edit - but if I try and make a link it won't allow it.

Getting more disheartened as the day rolls on.

---

### Post by robertc36 on 2007-06-29
Sorry am a noob myself

NTFS    [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/) will mount and allow you to change permissions.
To change permissions for other folders have been using the chown command.

> ie sudo chown you@you /folder/   etc

sorry if does not appear correct am still learning this stuff myself

---

### Post by forestpixie on 2007-06-29
yes thanks I know about that 

i have that installed and configured 

once I had permission but after a reinstall it's all gone belly up!

---

### Post by forestpixie on 2007-06-29
bump

---

### Post by forestpixie on 2007-06-29
I've succeded in getting permissions for me for both drives - but still if I try to make a link in the fat32 drive it gives me an error.

Any ideas

---

### Post by forestpixie on 2007-07-01
it's now ext3 - evrything is working (I believe)

---

