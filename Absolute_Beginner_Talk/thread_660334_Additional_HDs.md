---
title: "Additional HDs"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-01-06
I just installed Feisty on my friends desktop (only cuz I had that CD, I'll upgrade to Gusty later tonight) but he's got a 90gb ATA, a 160gb ATA, and a 500gb SATA.

I split the 90gb into two even partitions and put ubuntu on one (he wants to put XP on the other).  I'm sure I didn't 100% set up all the HDs when I did the graphical install cuz sometimes that stuff gets confusing but I can only see the FileSystem (45gb) within linux.  I haven't installed XP yet and, frankly, I'm not in a hurry.

45gb - ext3
45gb - unallocated space

160gb - formatted at FAT32 during graphical installation

300gb SATA - didn't touch (he needs the info on that drive)

I'm sure it has to do with the Mounting Point but I'm going to need a bit more direction...

---

### Post by PeterJS on 2008-01-06
Looks good, what's the problem are some of the drives not showing up in /media/ ?

---

### Post by cartisdm on 2008-01-06
> **PeterJS said:**
> Looks good, what's the problem are some of the drives not showing up in /media/ ?

yeah they are not showing up so how do I get to where I can access them within Ubuntu?  At least the 160 since I formatted it in FAT32 so I could share the contents with XP

---

### Post by cartisdm on 2008-01-09
I've checked within the POST and all the harddrives are recognized so I really just need to find out how to get Ubuntu to recognize it

---

### Post by PeterJS on 2008-01-09
Have you looked in /media/ ubuntu's pretty good about mounting everything it can.

If not **fdisk -l** should print out a list of all the device nodes for your paritions and what file system they are using. From this list you could add entires to /etc/fstab for them:
```

/dev/something /mnt/somewhere defauts 0 0

```
You may need to change the flags from defaults, as to which ones you'd need with out more information (likely by trial and error) I can't say.

I assume the 300gb drive is ntfs, you probably want to use [ntfs-config](apt:/ntfs-config) to set up the entry for that drive.

---

