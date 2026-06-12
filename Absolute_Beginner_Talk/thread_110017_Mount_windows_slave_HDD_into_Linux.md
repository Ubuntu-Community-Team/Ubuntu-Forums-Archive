---
title: "Mount windows slave HDD into Linux"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by corlex on 2005-12-29
Hello.
I am now trying to mount my other HDD that is already ONE windows partition. with some files I can read.
If you already have understand me right, I have 1 secondary HDD that is one windows partition (250 GB), and I want to read those files. But I can't fix it.
It is an ntfs windows partition.

anyone? :)

---

### Post by Gimbo on 2005-12-29
[http://ubuntuforums.org/showthread.php?t=109954]("http://ubuntuforums.org/showthread.php?t=109954")

Have a look at that thread first.
I think you need to create a line like the
```

/dev/hda1 /media/windows ntfs umask=0222 0 0

```
line, but with hdb1 rather than hda1. As far as I know, hdb1 refers to the second physical hard drive's first partition, which should be your windows partition on the slave hard drive.

I'm extremely new, though, so that probably won't work.

---

### Post by JimmyBEng on 2005-12-29
gimbo's solution should work if i understand correctly.

after creating the line in the fstab file. run this command to mount all the partitions listed in the fstab.
```
sudo mount -a
```

---

