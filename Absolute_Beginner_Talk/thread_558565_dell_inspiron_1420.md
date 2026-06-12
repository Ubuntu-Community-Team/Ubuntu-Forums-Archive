---
title: "dell inspiron 1420"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by morris71 on 2007-09-24
Hi All,

i have a brand dell inspiron 1420 new just delivered with Vista pre-installed.

I have created 4 partitions as suggested in this forum: 1 vista (ntfs), 1 data (ntfs), 1 /swap 1 linux ext3.

I have DLed 7.04 (both 64bit and 32bit versions) and start installing it. everything is fine until the "install base" step, here i have a series of messaging "package <name> error" and suggest press enter to continue and after a few a message that install base fail and jump into  main menu with only option to abort installation.

any suggestions, idea, help to solve this issue. much appreciated folks!

morris
london, UK

---

### Post by por100pre1 on 2007-09-24
Check  Ubuntu CD for errors, make space for Ubuntu and use the largest free space option and let the CD take care of partitioning. Read [here]("http://ubuntuforums.org/showpost.php?p=3412810&postcount=3") for more.

---

### Post by morris71 on 2007-09-24
thank for your reply.
to answer:
- i have checked both CD .iso and no errror (with chechsum application)
- for ubuntiu i reserved 10GB, swap 2GB, data 50GB, vista 40GB
as said i have partinioed with ext3 and /swap partion with linux installer (during installation process), then i did users step, then when we enter in install base step the series of errors mentioning "packages errros" came out and it forced me go out from installation process -? main CD menu and the only hing i can do it was abort and reboot.
i hope this clarify and let me know if you need more details.

thanks again.

mn

---

### Post by WAB on 2007-09-24
I installed Feisty form a remastered version for Inspiron series. I have a 1420, and it works perfect

[http://linux.dell.com/dru/images/](http://linux.dell.com/dru/images/)

I didn't change the original partition system, only shrinking a small amount of space of original windows C:, enough for ubuntu install.

I had some troubles with dual boot, because I didn't want to write my original MBR, but using easybcd.exe, the problem was fixed.

Everything is working, except mic, and currently I'm trying install my webcam.

Regards.

---

