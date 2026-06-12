---
title: "Evolution addybook and signatures &quot;permission denied&quot;"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by argraff on 2008-03-15
Hi all - looked everywhere for this, but no luck.

I recently added a new user to my Ubuntu for the purposes of separating work and play. I backed up my .evolution folder, moved it to my new username's desktop, restored it, and now things are screwy.

I can send and receive, change my calendar and to do lists, but get a "permission denied" on changing my address book, my signature and probably other things. 

I checked all of the permissions. They are identical to my old ones, with the exception of the owner, which I changed myself. Listed below: 'andy' is the original, 'argraff' is the new user.

```
argraff@gwilym:~$ ls -l /home/andy/.evolution/
total 148
drwxr-xr-x 4 andy andy  4096 2008-03-11 16:57 addressbook
-rw-r--r-- 1 andy andy 46576 2008-03-14 11:46 backup-restore-gconf.xml
drwx------ 5 andy andy  4096 2007-09-30 21:10 cache
drwxr-xr-x 5 andy andy  4096 2008-03-12 17:56 calendar
-rw------- 1 andy andy     2 2008-03-14 14:21 camel-cert.db
-rw-r--r-- 1 andy andy  3230 2007-11-09 10:10 categories.xml
-rw------- 1 andy andy 65536 2008-03-13 13:45 cert8.db
-rw------- 1 andy andy 16384 2008-03-13 13:45 key3.db
drwxr-xr-x 7 andy andy  4096 2008-03-13 17:08 mail
drwxr-xr-x 5 andy andy  4096 2008-03-11 16:57 memos
-rw------- 1 andy andy 16384 2007-07-10 13:09 secmod.db
drwx------ 2 andy andy  4096 2007-09-09 11:27 signatures
drwxr-xr-x 5 andy andy  4096 2008-03-13 17:08 tasks
argraff@gwilym:~$ ls -l /home/argraff/.evolution/
total 136
drwxr-xr-x 4 argraff argraff  4096 2008-03-11 16:57 addressbook
drwx------ 5 argraff argraff  4096 2007-09-30 21:10 cache
drwxr-xr-x 5 argraff argraff  4096 2008-03-15 10:47 calendar
-rw------- 1 argraff argraff     2 2008-03-15 10:47 camel-cert.db
-rw-r--r-- 1 argraff argraff  3230 2007-11-09 10:10 categories.xml
-rw------- 1 argraff argraff 65536 2008-03-13 13:45 cert8.db
-rw------- 1 argraff argraff 16384 2008-03-13 13:45 key3.db
drwxr-xr-x 7 argraff argraff  4096 2008-03-15 10:47 mail
drwxr-xr-x 5 argraff argraff  4096 2008-03-11 16:57 memos
-rw------- 1 argraff argraff 16384 2007-07-10 13:09 secmod.db
drwx------ 2 argraff argraff  4096 2007-09-09 11:27 signatures
drwxr-xr-x 5 argraff argraff  4096 2008-03-15 10:47 tasks

```

Running evolution through the terminal yields no clues - it just says "permission denied."

Help! Many thanks in advance.

---

### Post by hhhhhx on 2008-03-15
maybey try sudo'ing it?

---

### Post by argraff on 2008-03-15
> **xhhux said:**
> maybey try sudo'ing it?

What do I sudo? I get the error when I'm using the gui.

---

### Post by glennric on 2008-03-15
Try running
```
sudo chown -R argraff:argraff ~/.evolution
```
from a terminal.  Then see if it works.

---

