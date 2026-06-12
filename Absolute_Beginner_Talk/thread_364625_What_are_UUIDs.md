---
title: "What are UUIDs ?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-02-18
What's the role of UUIDs in mounting partitions? 
Can't I use the /dev/whatever parameter instead of the uuids in the /etc/fstab file? Also how do i find the uuids of partitions (without peeking into the fstab file :) ) ?

---

### Post by solar george on 2007-02-18
They identify the file system. Similar to /dev/xxx but they will work if you have linux on a removable disk that may be used on more than one computer ( it might not get the same /dev/ on each computer)

Yes you can use /dev/hdxx if you not going to change you hardware setup soon.

The UUID of a file system is given to you after you create the filesytem
```
 $ mkswap /dev/hdax
Setting up swap space ect.......

Done 
UUID=fet2383hdj30od329d

```

I don't know how to find out on existing file systems.

---

### Post by rsambuca on 2007-02-18
To see all of your UUID's, enter this in a terminal:```
ls /dev/disk/by-uuid/ -alh
```

---

### Post by glotz on 2007-02-18
Try reading the man pages for mount and fstab for example. A nice little adventure... :lol:

---

### Post by drs305 on 2007-02-19
Does each thumb drive have it's own UUID, and does it ever change?  Currently my thumb drives mount under differing names depending on which computer I insert them. If I could put something in fstab so that whenever a specific thumb drive was automatically mounted it was always designated with the same name it would make my Unison scripts much easier to write.

---

### Post by dvarsam on 2007-02-19
[QUOTE=drs305]Does each thumb drive have it's own UUID, and does it ever change?  Currently my thumb drives mount under differing names depending on which computer I insert them. If I could put something in fstab so that whenever a specific thumb drive was automatically mounted it was always designated with the same name it would make my Unison scripts much easier to write.[/QUOTE]

Related Posts:

[http://ubuntuforums.org/showthread.php?t=286758](http://ubuntuforums.org/showthread.php?t=286758)

Good Luck!

---

