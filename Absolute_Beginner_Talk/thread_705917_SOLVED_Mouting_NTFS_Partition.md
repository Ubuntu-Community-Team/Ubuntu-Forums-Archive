---
title: "SOLVED: Mouting NTFS Partition"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by diaz028 on 2008-02-23
I installed Gutsy today, and for some reason my NTFS partition was not showing up on desktop or in PLaces->Storage.

So I finally found something that worked, Here it is...

> sudo mount -t ntfs-3g /dev/partition /directory/folder

Example:

> sudo mount -t ntfs-3g /dev/sda6 /home/user/Desktop/Storage

If that don't work, try this. But make sure you are willing to risk screwing something up here:

> sudo mount -t ntfs-3g /dev/sda6 /home/megan/Desktop/Storage -o force

Just wanted to help if anybody has this problem too.

-D

---

### Post by gimfred on 2008-02-25
well done, and congratulations on your altruism!

---

### Post by sayakb on 2008-02-25
@OP
I came to know about the force option when my external HDD refused to mount. So your last Code was exactly the thing Gutsy asked me to enter.. So din't have to scratch my head for long :)

---

