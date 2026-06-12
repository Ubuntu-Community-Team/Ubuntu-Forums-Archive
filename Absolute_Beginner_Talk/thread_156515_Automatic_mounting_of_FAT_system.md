---
title: "Automatic mounting of FAT system"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by wdbreen on 2006-04-07
Gday all,  i need some advice on an error i'm getting on startup.  I have added a line to the fstab file so that a FAT partition is mounted automatically on startup.  It reads like this:
/dev/hda6	/media/windows	vfat	iocharset=utf8,umask=0000	0	0

It works well, except that on startup the Linux boot sequence comes up with an error that the IO utf8 is not a valid charset for FAT.

So what is?  because it seems to work ok!

Breeny

---

### Post by aktiwers on 2006-04-07
Did you use this guide?

[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)

I have used it alot of times, and it has worked fine everytime.

---

### Post by wdbreen on 2006-04-07
Yes, i used this guide.  My line in fstab is basically a cut and paste of that tutorial!

But the error still occurs each time.  Just wondering what it means and maybe another way to satisfy the criteria.

---

### Post by frodon on 2006-04-07
I got the same error and i just don't use the parameter iocharset=utf8, nothing really important (my opinoin).

---

