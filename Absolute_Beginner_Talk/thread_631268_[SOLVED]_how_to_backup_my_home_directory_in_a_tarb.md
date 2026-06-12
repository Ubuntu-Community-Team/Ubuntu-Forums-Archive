---
title: "[SOLVED] how to backup my home directory in a tarball"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-12-04
I wanted to backup my home directory in a tarball 
how do i do this 
i tried 
```
 sudo tar -cZf /backup.tgz /home/arjayes/
```
but i get 
```

tar: compress: Cannot exec: No such file or directory
tar: Error is not recoverable: exiting now
tar: Removing leading `/' from member names

```
what is the right command

---

### Post by jken146 on 2007-12-04
bad advice edited out, sorry

Try the man page (man tar)

---

### Post by banewman on 2007-12-04
Try - 
tar -cvzf /backup.tar.gz /home/you
 The  v  is for verbose  - lets you know where you  went wrong and try with no  /  on the end.  :)

---

### Post by ubukool on 2007-12-04
Hi,

Check out this excellent article:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

So I guess it would be:

tar cvpzf /backup.tgz  /home/arjays

:) good luck

---

### Post by arjayes on 2007-12-04
thanks that solved it :)

---

### Post by ukripper on 2007-12-04
p will preserve your permission if you want to restore simply replace z with j (if bz2) ortherwise let it be z and c with x

example: tar xvpjf {yourBackup} {RestoreDirectory}

---

