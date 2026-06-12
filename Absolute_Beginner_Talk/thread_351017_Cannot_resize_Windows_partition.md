---
title: "Cannot resize Windows partition"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-02-01
I dual boot with Windows XP, and I want to resize that partition so my Ubuntu partition has more space. However, GParted on the Live CD cannot resize the XP partition as 'the device is busy.' How do I get around this problem so I can resize the partition?

Thanks inadvance

---

### Post by bodhi.zazen on 2007-02-01
> **spamzilla said:**
> I dual boot with Windows XP, and I want to resize that partition so my Ubuntu partition has more space. However, GParted on the Live CD cannot resize the XP partition as 'the device is busy.' How do I get around this problem so I can resize the partition?

Thanks inadvance

Unmount the (windows) partition.

In a terminal:
```
sudo umount /dev/hda1
```

FYI, you should defragment the partition from Windows before you resize ....

---

### Post by spamzilla on 2007-02-01
What could happen if I don't defrag the Windows partition?

Thanks for the help, mate :)

---

### Post by Coelocanth on 2007-02-01
If you don't defrag, you may have pieces of files and data spread across the disk. I recommend defraggging at least twice (I did it 3 times when I resized my Windows partition). If you resize and end up erasing data, you could lose some or all ability to retrieve it.

Back up any important data before resizing as well. There are no guarantees when it comes to resizing partitions.

---

### Post by Crakie on 2007-02-01
> **spamzilla said:**
> What could happen if I don't defrag the Windows partition?

Thanks for the help, mate :)

Bohdi assumed your Windows partition was the first one, which is probably the case. The part of that partition you use to enlarge the Ubuntu one, should not contain any files, else resizing will fail. Defragging will put the files at the beginning of the Windows partition, hence increasing the chance of success for resizing it. Note that even defragging might leave a few clusters occupied in places where you don't want them to be, which might still result in interference. This is very annoying, although repeated defragmentations might help.

---

### Post by Pugwash on 2007-02-01
For the defrag, download a defrag program called perfectdisk, then defrag using the "free space consolidation" option. Then uninstall the program. Then install ubuntu.

---

