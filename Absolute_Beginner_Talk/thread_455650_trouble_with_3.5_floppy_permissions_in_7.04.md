---
title: "trouble with 3.5 floppy permissions in 7.04"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by martianvamp on 2007-05-26
I installed 7.04 and can't get the permissions to read and write my 3.5 floppy, only read.
Anyone had the same problem?

---

### Post by hasimir44 on 2007-05-26
I don't have any floppies to test reading or writing but.. 

you can start by checking your   /etc/fstab file..

```
cat /etc/fstab
```

 it should have an entry like this: 

```

<file system>  <mount point>       <type>       <options>        <dump>  <pass>

/dev/          /media/floppy0      auto        rw,user,noauto       0       0
```

the "rw" and the "user" in the options section should give you read/write. if you have these already, then maybe it's the permissions for your /media/floppy0 directory.. try this: 

```
ll -d /media/floppy0
```

it should yield something like this: 

```

drwxr-xr-x 2 root root 4096 2006-11-07 00:35 /media/floppy0

```

my permissions will only allow root to write, but anyone should be able to read.. if your perms are the same, then you should be able to write as root also..

---

### Post by martianvamp on 2007-05-26
thanks. I'll try it and let you know.

---

