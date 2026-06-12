---
title: "DOH! partition help please"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by heathen on 2006-09-30
Ok, I had to reinstall windows a while back and set Ubuntu to dual boot again.  While reinstalling Ubuntu I accidently made windows 3/4 of the disk instead of the other way around.  So, I got bored today, resized my windows partition, Made a second ext3 partition, got the drive mounted, now I dont have write access.  What am I missing?

I used the wiki's tutorial for the automounting found [here]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

using dapper btw..

---

### Post by tagra123 on 2006-09-30
This might help

```
sudo gedit /etc/fstab

```

For FAT partitions use a line like this 
```
/dev/hdd3  /media/linwinshare vfat defaults,utf8,umask=007,gid=46 0 1
```

For EXT3 Partitions use a line like this:
```
/dev/hdb1       /media/tempdrive    ext3   defaults               0  2
```

The numbers at the end can be changed to 0 -- Its just telling linux how to check the disk

---

### Post by heathen on 2006-09-30
tried that... nothing changed... thru a few hours of various keywords and the forums I ended up getting it done...  using nautilus i changed the group for the disk to my username... now i can read/write..  i just got it, but thanks for the reply..

---

