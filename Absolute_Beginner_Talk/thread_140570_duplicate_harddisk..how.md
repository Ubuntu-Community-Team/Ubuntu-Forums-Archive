---
title: "duplicate harddisk..how?"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by mukh_86 on 2006-03-06
i want to know how to duplicate a harddisk....all of the hard disk...include the os.it is possible?

can harddisk being duplicate as a key duplication?how to do that?anyone?:-k :-k :-k

---

### Post by shof2k on 2006-03-06
If you want to make a duplicate copy of ubuntu, you can follow this guide.
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087).

---

### Post by mukh_86 on 2006-03-06
i want to backup a server setting using fedora4...can i?

---

### Post by aysiu on 2006-03-06
[QUOTE=mukh_86]i want to know how to duplicate a harddisk....all of the hard disk...include the os.it is possible?

can harddisk being duplicate as a key duplication?how to do that?anyone?:-k :-k :-k[/QUOTE] Use [PartImage](http://www.partimage.org). If you have the Universe repositories enabled... ```
sudo apt-get update
sudo apt-get install partimage
sudo partimage
```

---

### Post by steve.horsley on 2006-03-07
To take a complete disk image, use dd. I do this for my XP partition, like this:
**dd if=/dev/hda2 of=win-partition-image**
Of course, this is only a partition image. To image an entire disk, use something like **if=/dev/hda** instead. What dd gives you is a bit-for-bit image, no compression, no skipping of unused blocks.

---

### Post by Cyril on 2006-05-15
How do you restore the partition/disk from the image?

---

### Post by et2013 on 2006-05-15
I think that would be something like :
**dd of=/dev/hda2 if=win-partition-image**

Someone correct me if I'm wrong

---

