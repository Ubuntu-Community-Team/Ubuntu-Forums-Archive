---
title: "find - command question"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-02-16
Is there a way to use the find command to only search linux partitions?
Lets say I wanted to find any files named grub.*  but I only want to look in linux for it.
I use --   find /  -iname  "grub.*"  but it still searches the   /media/(windows drives) 
It takes a lot more time searching hundreds of gigabytes that I don't want on my widows drives.
Could I tell it just to search ext3 files?

---

### Post by wolfen69 on 2008-02-16
```
locate name_of_files
```

---

### Post by dcstar on 2008-02-16
> **garyed said:**
> Is there a way to use the find command to only search linux partitions?
Lets say I wanted to find any files named grub.*  but I only want to look in linux for it.
I use --   find /  -iname  "grub.*"  but it still searches the   /media/(windows drives) 
It takes a lot more time searching hundreds of gigabytes that I don't want on my widows drives.
Could I tell it just to search ext3 files?
Try:
```
find / -xdev -iname  "grub.*"
```
If you want to know what capabilities the command has: ```
man grub
``` will show you.

---

### Post by garyed on 2008-02-16
> **dcstar said:**
> Try:
```
find / -xdev -iname  "grub.*"
```


Thanks,
That's exactly what I was looking for.

---

