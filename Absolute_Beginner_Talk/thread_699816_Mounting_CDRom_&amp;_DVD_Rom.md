---
title: "Mounting CDRom &amp; DVD Rom"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by pemur1 on 2008-02-17
I really hate to post another problem with this, but I just can't figure it out. I switched from WinXP to Ubuntu over the weekend and haven't been able to get my CDRom & DVD drive mounted. I've read through some of the other threads regarding this and followed the instructions, but I still can't get them to work. Here's some of the information that was requested in the other posts:

root@xxxxxx-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=bee1a3ca-7187-4e6e-8873-883d8e3e6433 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0c333f6c-a4fb-450b-973a-4bb478274173 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Any help is greatly appreciated.

---

### Post by Presto123 on 2008-02-17
**Edit```
sudo mount /media/cdrom0
```**

Is not working, then?

---

### Post by pemur1 on 2008-02-17
> **Presto123 said:**
> ```
sudo mount /dev/hdd
```

Is not working, then?

No.

It says:

mount: No medium found

---

### Post by Presto123 on 2008-02-17
Sorry...I changed that above. Try that as well.

---

### Post by pemur1 on 2008-02-17
Now I feel like a complete idiot.

I accidentally put a DVD in the CDRom and a CD in the DVD player. No wonder I couldn't get them to work. Now, everything's fine. Sorry for the confusion. :)

---

### Post by Presto123 on 2008-02-17
LOL...Don't worry. The best of us do stuff like that! :P

---

