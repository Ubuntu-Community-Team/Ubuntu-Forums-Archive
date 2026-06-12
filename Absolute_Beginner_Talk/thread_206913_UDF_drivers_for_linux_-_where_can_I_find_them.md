---
title: "UDF drivers for linux - where can I find them?"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-30
Hi,

Does anyone know where to find UDF drivers for linux and how to install them?

I have some CDs and DVDs which I burnt in Windows using UDF and I can't open the in Ubuntu.

Thanks

---

### Post by falcon15500 on 2006-06-30
The solution might just be a simple change to your /etc/fstab or the way you are mounting them.  As far as I know, UDF should be fine as long as it is specified.

How are you mounting them?

What does your /etc/fstab look like?

falc

---

### Post by ovimunt on 2006-06-30
Here it is, etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/Data_Storage ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda1       /media/Windows_XP ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Well, I'm not sure how I'm mounting them... I just put the DVD in and that's about it. Then all I can see on the DVD is a text file which says that I should open it on a system that has UDF drivers...

> Please read this CD in a system with UDF reader driver.

---

### Post by ovimunt on 2006-07-01
*bump*

---

### Post by falcon15500 on 2006-07-01
Ahhh... Try this - I read this in a bug report.

Instead of **udf,iso9660** - use **iso9660,udf**
I know - looks odd, but apparently works.

falc

---

### Post by ovimunt on 2006-07-03
*bump*

---

### Post by jacquez on 2006-09-02
Thanks!  That worked for me.

---

### Post by Eric064 on 2006-09-06
Worked for me too!

---

### Post by Atomic Dog on 2006-09-06
I just made the setting auto.  If you read the bug reports more closely you'd have read that it seems to only accept the first argument ie. udf, iso9660 would make udf readable and iso9660 disks unreadable.  removing the two and inserting "auto" made everything work for me. :)

---

