---
title: "[SOLVED] noatime setting in fstab, good/bad..how to set?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by laidback on 2007-09-26
I have recently read about the setting option **noatime** that can be used in fstab to improve disc performance.

Does anyone have any experience of it?, is it considered OK to do?

As I'm very concerned re altering fstab here is mine, what would I do to switch on noatime for hda1?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1f9067aa-97a3-4de9-a4f2-84b6503ce58a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=d0cacd43-4643-4770-bfb9-fd4dc1c467e9 /media/hda3               ext3     rw,user  0    1
# /dev/hda5
UUID=123f582f-0971-434b-89ba-f1136cc0aaff none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Many thanks

---

### Post by jw5801 on 2007-09-26
atime is basically a tag that is placed on every block/file in a filesystem, which records the last time the file was accessed. Disabling this can increase the read time from your drive, as a write would not have to be done after every read.
To add it to your fstab, change the hda1 line to this:
```
# /dev/hda1
UUID=1f9067aa-97a3-4de9-a4f2-84b6503ce58a / ext3 defaults,errors=remount-ro,noatime 0 1
```

---

### Post by laidback on 2007-09-26
Thanks for this info. 

*Disabling this can increase the read time from your drive*

Isn't it meant to decrease the time taken rather than increase it, or have I misunderstood the purpose.?

---

### Post by asmoore82 on 2007-09-26
[SIZE="3"]Best Thread of The Month!![/SIZE]

little details like this are why I'm becoming addicted to the forums.
If anyone wants more information on the subject;
there is a log of master kernel hackers(Torvalds&Cox included) discussing the subject
and basically agreeing on how important this is for Server Performance under heavy loads
and Desktop Responsiveness in general: [http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148)

[SIZE="3"]Best Thread of The Month!![/SIZE]

---

### Post by insane_alien on 2007-09-26
> **laidback said:**
> Thanks for this info. 

*Disabling this can increase the read time from your drive*

Isn't it meant to decrease the time taken rather than increase it, or have I misunderstood the purpose.?

well, disabling noatime does decrease the performance, so he is right

thing he just worded  it a bit dodgily.

---

### Post by laidback on 2007-09-26
Many thanks for all this info. I've altered my fstab accordingly, so I'm hoping to notice an improvement now. Heart was in my mouth a bit as I rebooted but all is well.

Kindest Regards

Laidback

---

### Post by jw5801 on 2007-09-26
> **laidback said:**
> Thanks for this info. 

*Disabling this can increase the read time from your drive*

Isn't it meant to decrease the time taken rather than increase it, or have I misunderstood the purpose.?
heh. Yes, increase the **speed** of reading from the drive. I knew what I was trying to say, shouldn't post just before I go to sleep though. Apologies!

---

### Post by laidback on 2007-09-27
jw5801,

Thanks for the clarification. As you will have read I have added the option to my fstab file. Seems fine. Many thanks for your input.

Laidback

---

### Post by asmoore82 on 2007-09-27
this option can also be changed without rebooting with the command ...
```
~$ sudo mount -o remount,noatime /
```

---

