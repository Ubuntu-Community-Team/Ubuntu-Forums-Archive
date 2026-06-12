---
title: "Hidden partition"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by PuBiX on 2006-12-20
I have recently purchased a dell laptop and I plan on installing ubuntu on it, but I realized that there is a hidden partition loaded with recovery data. I was wondering if there was a way that i could back up that partition and burn it to a dvd.

---

### Post by kidders on 2006-12-21
Assuming it's small enough, you can. Note down the exact (down to the block) size of the partition, so you know how to recreate it, and dump it to a file. You can write the file back into an empty partition later, if you feel the need.

Something like this ought to do the trick:```
dd if=/dev/sda1 of=~/recovery_partition
```
That way, you'll have a byte-for-byte copy of the filesystem.

---

### Post by PuBiX on 2006-12-21
thanks man...ima try it out

---

### Post by steve.horsley on 2006-12-21
My inclination would be to leave that partition there. Just install Ubuntu in plac of the Windows partition.

---

### Post by kidders on 2006-12-21
Agreed :-) If you ever did want to put it back again, you'd only wind up having to delete whatever was using it's slot in the partition table.

---

