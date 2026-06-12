---
title: "Empty &quot;Temp&quot; cache?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by frogotronic on 2006-05-21
Hello,

  I've been using UBUNTU BB for about two months and I had a question about space.  Does Ubuntu/Linux cache web pages and videos, viewed as streams during browsing using Firefox?  I understand about clearing Firefox's cache, but does Ubuntu save videos to a different folder?  If so, how do I clear it out?

  I'm concerned about inadvertently filling up my HDD (which is only as a 10 GB partition).

Also, where can I view the space used/space available in Ubuntu BB?

- CH

---

### Post by Klaidas on 2006-05-21
Well, all that catche, as far as I understand, is saved in /tmp, but gets cleared after reboot.
For viewing used and space left:
> df
I might be mistaken, because I\m not on my ubuntu box right now

---

### Post by macdo on 2006-05-21
Use ```
df -h
```
That gives you human-readable sizes...

---

### Post by frogotronic on 2006-05-23
[QUOTE=macdo]Use ```
df -h
```
That gives you human-readable sizes...[/QUOTE]

Great, thanks.

What's the "tmpfs" directory?

- CH

---

### Post by macdo on 2006-05-23
tmpfs = TeMPorary File System

[quote=Linux Headquarters]+Tmpfs is a file system which keeps all files in virtual memory.
+
+
+Everything in tmpfs is temporary in the sense that no files will be
+created on your hard drive. If you unmount a tmpfs instance,
+everything stored therein is lost.[/quote]
[http://www.linuxhq.com/kernel/v2.4/17-pre5/Documentation/filesystems/tmpfs.txt](http://www.linuxhq.com/kernel/v2.4/17-pre5/Documentation/filesystems/tmpfs.txt)

---

