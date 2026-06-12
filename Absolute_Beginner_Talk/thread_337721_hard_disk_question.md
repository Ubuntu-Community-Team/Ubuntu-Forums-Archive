---
title: "hard disk question"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by aoreste on 2007-01-13
Hi. i have 2 hard disks and if i'm not mistaken they are listed under /dev as hdb and hdb1.
One of them is formatted and running the ubuntu installation and the other one is unformatted. is there a command that helps me find out which is which?

also, if i want to format it the command is mkfs.ext2, right?

thanks

---

### Post by taurus on 2007-01-13
Actually, the first harddrive, master drive, is known as /dev/hda, while the slave drive is called /dev/hdb.  Open a terminal, Applications -> Accessories -> Terminal, and run this command and it will tell you.

```
sudo fdisk -l
```

---

