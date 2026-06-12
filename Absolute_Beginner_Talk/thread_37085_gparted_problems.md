---
title: "gparted problems"
date: 2005-05-25
forum: Absolute Beginner Talk
---

### Post by bobgreen5s on 2005-05-25
I am trying to resize my NTFS windows partition and then resize my linux EXT3 partition to add some space. When I load gtparted or qtparted the options resize & move are blanked out. I tried unmounting the partition with no luck.


Screenshot attached.


Any help is appreciated.

---

### Post by Xian on 2005-05-25
You'll need to unmount those partitions before you can edit them.
Notice the lock symbols in the gparted screen.

---

### Post by bobgreen5s on 2005-05-25
[QUOTE=bobgreen5s]I tried unmounting the partition with no luck.[/QUOTE]

Tried that already. :(

---

### Post by Xian on 2005-05-25
What is the output of this command:

```
$ sudo umount /dev/hda1
```

---

### Post by Xian on 2005-05-25
BTW, I don't think you can feed space from that NTFS primary partition directly into a subpartition that is located within your /dev/hda2. You will likely have to resize the /dev/hda2 first and then feed out space from that, but this will AFAIK entail newly formating all the partitions under it as well.

---

### Post by TravisNewman on 2005-05-25
I don't think that's correct. Not sure, its been a while, but I do remember expanding an extended partition and then expanding the logical drives under it as well. With plain parted, not sure about the graphical tools, and how well they interact.

---

### Post by Xian on 2005-05-25
[QUOTE=panickedthumb]I don't think that's correct. Not sure, its been a while, but I do remember expanding an extended partition and then expanding the logical drives under it as well. [/QUOTE]
Yeah, you very well could be right. That is likely the correct order.

Try expanding your hda2 first, bobgreen5s. 
Then see if you can edit the desired partition below that.

You'd have to use a Live or Install Linux CD, or a Windows application.
Since you can't edit a partition that you are operating in like Ubuntu.

---

