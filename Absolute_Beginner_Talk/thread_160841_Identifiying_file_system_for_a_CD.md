---
title: "Identifiying file system for a CD"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by utab on 2006-04-15
Dear all,

when I type 

mount -t iso9660 /dev/hdb/ /cdrom

I got 

mount: special device /dev/hdb does not exist

message. 

/dev/hdb is for non SCSI type cdrom but how can learn mine??

any ideas.

---

### Post by 5-HT on 2006-04-15
To find out what your CD/DVD drive is getting recognized as, what about trying something like:
```
 dmesg | grep -i cd 
```

---

