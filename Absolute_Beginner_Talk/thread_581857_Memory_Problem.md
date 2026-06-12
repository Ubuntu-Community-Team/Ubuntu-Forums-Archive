---
title: "Memory Problem"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by licker4450 on 2007-10-19
I keep running out of memory when I download movies off the internet.  I am downloading them into my home folder.  Unfortunately, it only allows 8 GB in that area.  I have an 80 GB hdd of which most is in the under my media/disk.  However, nothing can be saved in there.

Any suggestions.

---

### Post by mlentink on 2007-10-19
> However, nothing can be saved in there.
Why not? What error messages do you get?

---

### Post by bapoumba on 2007-10-19
What is the output of
```
cat /etc/fstab
```
May be the partition is owned by root, and a regular user cannot write on it.

---

### Post by licker4450 on 2007-10-19
Here is what it says.

---

### Post by mlentink on 2007-10-19
Dennis could you tell us what kind of a harddisk this is? Is it USB by any chance? Because your system doesn't see it, so no wonder you can't save anything to it.

---

### Post by licker4450 on 2007-10-19
No it is not an external drive.  It is a new internal hard drive that was installed some time ago.

Is there anything that can be done to make Ubuntu see it.

Thanks

---

