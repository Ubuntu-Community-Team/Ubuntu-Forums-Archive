---
title: "Back up drive"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-03-12
Hi!

I have an old IDE drive I just stuck into my case.  I'd like to set that up to be a dedicated "back up" drive.  What's the best way to format it and mount it as a read/write mass storage type of thing?

Good night,
Brian

---

### Post by chuckyp on 2007-03-13
If you are just using linux I would format as ext3.  If you are dual booting with windows and want both os's to use the drive use fat32.

---

### Post by marmaladejackson on 2007-03-13
Yeah, ext3 will work just fine.  What program do I use?

---

### Post by xyz on 2007-03-13
Don't forget not to format a mounted partition...so a Live CD, Gparted, for instance.

---

### Post by marmaladejackson on 2007-03-13
OK.  Was able to mount the ole' IDE by appending my fstab thusly:

[B]#
#mounting IDE
#
/dev/hdc1 /media/ide
[/B]

The is a bunch of junk on it from a previous botched install attempt.  I can't delete it as I do not have permission.  What can I add to the above to make it universally read/write able?

Thanks again... making progress everyday!
-B

---

### Post by marmaladejackson on 2007-03-13
For that matter, how would I change permissions on a USB drive?

---

