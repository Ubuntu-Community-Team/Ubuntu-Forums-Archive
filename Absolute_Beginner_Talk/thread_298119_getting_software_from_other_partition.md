---
title: "getting software from other partition?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by davidleeroth2006 on 2006-11-12
I am using a dual boot on my laptop! and I would like to use the software installed on my windows xp partition. I would like to use Dreamweaver (and other macromedia products) Eclipse (java ide) and MS Access.
Is it possible to use the software from the other partition without installing it on the ubuntu partition?
With Eclipse I have all my java files on my windows desktop, and so ideally I would like to access those files and have them update when I add or modify code in Eclipse while using ubuntu!
Is this all possible?

---

### Post by bulldog on 2006-11-12
Think you have to dive in 'wine'.

Don't use it myself but it let you run certain window programs on linux.

---

### Post by davidleeroth2006 on 2006-11-12
Does anyone else know for certain

---

### Post by davidleeroth2006 on 2006-11-12
or if I had to install eclipse again could I still access my folder from windows?

---

### Post by kinematic on 2006-11-12
as you probably konw windows apps don't run natively on linux so you'll have to use a windows emulator.

---

### Post by davidleeroth2006 on 2006-11-12
well I have 3gb left on the ubunut partition so I will install dreamweaver, flash and eclipse on there!
But still..... can I access my java files from the other partition and it updated the contents regardless on which OS I am writing them on?

---

### Post by bulldog on 2006-11-12
You can't write to your NTFS partition,if you meant that.

It's read only by default but there are ways to enable it on your own risk of course.

But I'm not a user of such programs so I can't really help you with these things.

---

### Post by kinematic on 2006-11-12
if by updating you mean writing to your java files on your ntfs partition.....it is possible with the ntfsg3 driver for linux.
it is claimed to be safe but since i don't have a ntfs partition i can't comment on it.

---

### Post by davidleeroth2006 on 2006-11-12
Eclipse the ide saves all the files in a folder, and so when you load eclipse all your java projects are availabe. I could have eclipse have its own folder on ubuntu but that would mean having two sets of java files on each os. Could become a problem (unless I  stick with one OS, which is not likey atm).

---

### Post by bulldog on 2006-11-12
You can make a small FAT32 partition to use it in ubuntu as well in XP,they both can read and write a FAT32 file system.

---

