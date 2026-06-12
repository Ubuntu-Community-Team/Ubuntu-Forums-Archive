---
title: "no root file system is defined"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-05-19
I have all my partitions set up like so:

Device        Type   Mount Point   Size              Used
/dev/sda
/dev/sda1   Fat16  /media/sda1         49  MB        33 MB
/dev/sda2   ntfs     /media/sda2   10737  MB    4500 MB
/dev/sda3   ntfs     /media/sda3  149251 MB  18300 MB
/dev/sda5   ext3   /home               34998 MB  Unknown
/dev/sda6   ext3   /root                 10001 MB  Unknown
/dev/sda7   ext3   /swap                 1998 MB  Unknown

I click Forward and get this:  No root file system is defined. Please correct this from the partitioning menu.

Whats the deal??

Thanks, Alain

---

### Post by Seisen on 2007-05-19
Try changing it from /root to just / and see if it works.

---

### Post by S15_88 on 2007-05-19
yes figured that out, changed it to jus "/".  Now it asks for a swap partition, how come the one i have there isn't working?

Thanks, Alain

---

### Post by Seisen on 2007-05-19
The file system should be "swap" instead of "ext3"

---

### Post by S15_88 on 2007-05-19
haha oh man can't believe i missed that good call haha

Thanks, Alain

---

