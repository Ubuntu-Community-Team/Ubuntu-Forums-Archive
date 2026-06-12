---
title: "disk usage -du"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by DisruptiveTechnology on 2007-11-28
Hi

I am having trouble getting a full account of folders that seem to be large. I am using the following command: du -s -h *.*

However I find that all directories are not listed. How do I change this so that I get all files/folders?? Or force all files/folders to be read? I cannot use a graphical environment as this is on a server.

Thanks

B

---

### Post by moyazes on 2007-11-28
try using 'find' in a terminal.

example:

 find /home/alex -size +10000

more details can be found from the man pages

$man find

hope this helps.

moyazes

---

### Post by nick_h on 2007-11-28
Just use:
```
du -h
```

---

