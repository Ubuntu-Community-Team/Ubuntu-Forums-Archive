---
title: "What means the &quot;@&quot; after the file permissions?"
date: 2010-06-15
forum: Apple Hardware Users
---

### Post by schaert on 2010-06-15
Hello everybody,

First of all, many thanks to this great community which helped through a lot only by being a reader - now it was the time to register and ask a question myself. Maybe somebody can help me.

I have a Ubuntu 10.04 server at home with an additional FAT32 hard disk. From this disk I copied all the contents to an external FAT-disk, then formatted the server's FAT-disk to an ext4. I then tried to move back the content from the external disk to the ext4. However, I always get errors telling me I don't have the permissions needed to do so. I move the files using samba, and I think I got the idea of samba and how to use and administrate it. What I'm currently wondering about is the following:

-rw-r--r--@   1 Tom  staff    67385344  4 Sep  2009 movie.avi

What means the "@" symbol after the file permissions? I don't think it's the sticky bit, but I've never seen this before. It happens that the permission error always shows up when trying to copy/move files with the "@". Please note that only a minority of the files have the "@".

Any idea? Thanks for your help in advance.

Regards from Switzerland,
Thomas

---

### Post by schaert on 2010-06-16
Well I found out myself. It indicates that there are extended attributes, and they prevented me from copying those files having these attributes to another location.

Just in case anybody else has the same question.

Regards,
Thomas

---

