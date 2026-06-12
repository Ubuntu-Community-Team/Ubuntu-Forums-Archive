---
title: "accessing files on CD in terminal?"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by bazcor on 2005-12-30
Hello, I've been trying unsuccessfully so far, to access files on a CD rom from terminal. The CDROM icon appears on the desktop, but navigating there and doing ls -a doesn't show it. Where am I going wrong? I'm sure this is a simple one.

Thanks for any replies .. Barry

---

### Post by bazcor on 2005-12-30
OK I just found it, I should have examined the filesystem more carefully!

---

### Post by lleb on 2005-12-30
what path are you navigating to?

IIRC default for unbuntu is /media/cdrom1 or /media/cdrecord0 or something like that.

you can tab to finish and get the list of what is avaliable:

/media/cd

at that point hit the tab 2 times real fast.  then you will get a list looking like:

```
user@p4ssmahome:~$ cd /media/cdrom
cdrom/  cdrom0/ cdrom1/

```

then i can pick the correct one that my disk is in.

good luck.

---

