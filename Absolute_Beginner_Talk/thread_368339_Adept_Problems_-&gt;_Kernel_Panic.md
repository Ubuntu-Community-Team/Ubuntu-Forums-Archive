---
title: "Adept Problems -&gt; Kernel Panic"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2007-02-23
Hello there! Yesterday I was trying to update my ubuntu (6.10), and there was some kernel updates. After adept completed the process it thrown an error saying that was not possible to commit the changes. Today when I tried to boot I was getting an kernel panic: Can not mount VFS on /root or something like this. I chose a different kernel at grub menu, and I'm ok now. But when I try to run adept I get an error about another process being using the database. There's no process trying to use the database, I'm wondering if could be some kind of locking of the file (I used to get it from fedora on RPM). If so, how do I unlock the file?

Best Regards

---

### Post by viniciuscarvalho on 2007-02-23
Never mind...
dkpg --configure -a fixed everything

---

