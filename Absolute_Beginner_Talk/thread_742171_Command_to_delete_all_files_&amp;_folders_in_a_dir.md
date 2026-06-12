---
title: "Command to delete all files &amp; folders in a directory (using SSH)?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-04-01
Hi,

I would like to delete all files & folders in a directory I am viewing using SSH.  

How would I delete all the folders in /shares/internal/PUBLIC/Network Backup Drive ?

If I was navigated to that folder already?

Thanks,
Rich

---

### Post by pytheas22 on 2008-04-01
```
rm -r *
```

should do it.  If you don't own/have right permission to some of the files you would need to use sudo, if you are allowed.

---

