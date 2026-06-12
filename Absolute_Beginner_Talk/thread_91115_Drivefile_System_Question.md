---
title: "Drive/file System Question"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by Stormspace on 2005-11-16
I have multiple drives in my PC. Does linux see these drives and mounted File Systems as one contiguous space?

---

### Post by Kyral on 2005-11-16
In a way. It knows they are on different drives/partitions, so if you try to overfill something it will know and stop you. However the filesystem hierarchy is "transparent". Meaning that you can't tell that you jumped from a drive to another unless you know it. Case in Point...

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb2             6.5G  279M  5.9G   5% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-9-k7/volatile
/dev/sda1             154G  146G  365M 100% /anime
/dev/hda3             266G   56G  210G  21% /home
/dev/hda1             9.4G  2.5G  6.9G  27% /usr
/dev/hda2             4.7G  1.3G  3.5G  27% /var

```

Notice how my drives and partitions are spread out. Now Linux knows this, but when it comes to copying files and moving through the filesystem, you wouldn't know it. Get what I am trying to say?

---

### Post by Stormspace on 2005-11-16
So, to the user its one big space.

---

### Post by Kyral on 2005-11-16
Yah, in a word :P But the disk monitoring apps will show multiple HDs still.

---

