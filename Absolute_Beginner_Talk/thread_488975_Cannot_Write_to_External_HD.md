---
title: "Cannot Write to External HD"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by jmusso on 2007-06-30
Picked up a Western Digital 120gb external HD the other day. Partitoned it with a small, 10gb Fat32 partition to keep fs-driver on so if I connected it to Windows computers, I could enable them to access the ext3 partition, which is the rest of the HD. It worked great, I sent all the stuff on my old Windows partition onto the ext3 partition, and am able to read them fine from Ubuntu. However, I can't write to the drive. Can someone help me?

---

### Post by Computer-Geek on 2007-07-01
Which drive EXT?
If External (EXT) then there is a problem in linux i think so becoz i couldn't write on a FAT32 partition too with linux.

Thanks!!

---

### Post by vpjr on 2007-07-01
hi,

what's the output of:

mount

?

regards,

ven

---

### Post by Dive4Life on 2008-01-11
Having the same problem as well.  My drive has successfully mounted, but I cannot, for the life of me, write to the darn thing.  It says that my file system is hfsplus, I thought it was NTFS.  I also know that I don't have permission.  I thought I had changed that, but it isn't showing up.  This is extremely frustrating to say the least.  Please, someone help.

---

### Post by jslmg on 2008-01-22
Yes, same here. My external drive is an "hfsplus" filesystem.I want to edit tags, for example, in Rhythmbox to take out all the "unknown"s in the blank fields, but can't, cuz it's a "read-only filesystem." I want to add audio files to the drive, too, but can't.

Any ideas?

---

