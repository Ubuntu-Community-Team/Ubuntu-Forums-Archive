---
title: "Help me Hose a flash disk"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-09
Hey guys

I have a 256mb UFD that i dont really need, and i wanted to partition it, and install Damn Small Linux on the second partition, to have a solid live linux, and to use on other computers etc

So, I reformatted the drive, as 2 partitions, BUT I FORGOT TO UNMOUNT IT FIRST.

Now, i *can* unmount it.... but i get an error telling me that the device cant be stopped (i have resolved my issues with feisty unmounting USB drives... so thats not it).

And my fdisk shows me it HAS been partitioned:
```

Disk /dev/sdb: 258 MB, 258998272 bytes
16 heads, 32 sectors/track, 988 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         494      126448    b  W95 FAT32
/dev/sdb2   *         495         988      126464   83  Linux
```

But I get the feeling thats NOT the case... because when i plug it back in, the 2 or 3 files i had on there are STILL there (and I created 2 new partitions).

Now, I think the problem is that its not unmounting properly, and as such, i cant partition it (i tried again after unmounting it, and i got an error message from fdisk).

Does this make any sense?

Could anybody give me any good advice, on how to totally hose it, and start again?

If it becomes ruined, i dont care ;)

drowner

---

### Post by Schalken on 2007-05-09
I don't quite understand, but to simplify things, just use gparted (apt-get install gparted) and it will handle the unmounting etc.

---

### Post by drowner on 2007-05-09
cheers schalken.

I'll post what happens here as an educational session ;)

I thought i had it all done with fdisk... but oh well. A lesson learnt.

---

### Post by drowner on 2007-05-09
Ok good!

```
Disk /dev/sdb: 258 MB, 258998272 bytes
255 heads, 63 sectors/track, 31 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          14      112423+   b  W95 FAT32
/dev/sdb2   *          15          31      136552+  83  Linux
```

Looks nice!

I've put the boot flag in the right place... a question, out of curiosity.... when i closed gparted, ubuntu automatically mounted the FAT32 partition, but not the ext3 partition.

Is this normal? Is there a reason why?

---

