---
title: "cannot mount volume?!"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by The Hogg on 2008-04-05
Just installed Ubuntu and having problems accessing my 2nd hard drive (where all data is stored, safely away from whatever OS I have...)

I get the following error message:

[http://i27.tinypic.com/xlcf36.png](http://i27.tinypic.com/xlcf36.png)

Any ideas how to get this mounted? I have tried doing what it says in the window:

Sudo mount -t ntfs-3g /dev/sdb1/mount/disk -o force

and nothing happens!

---

### Post by northern lights on 2008-04-05
Most likely you're dual booting Windows also, right?!

In that case, you most likely had your harddrive (or whatever device it is) connected to Windows before and either simply unplugged it or shut down your comp by just killing power.

Connect your device, boot into Windows (login screen suffices) and do a clean exit ("shutdown windows"), with the device connected. Boot Linux. Works.

---

### Post by billgoldberg on 2008-04-05
> **northern lights said:**
> Most likely you're dual booting Windows also, right?!

In that case, you most likely had your harddrive (or whatever device it is) connected to Windows before and either simply unplugged it or shut down your comp by just killing power.

Connect your device, boot into Windows (login screen suffices) and do a clean exit ("shutdown windows"), with the device connected. Boot Linux. Works.

Yes, it's a dual boot thing.

You should disconnect the hardware correctly in windows, or ubuntu can't mount it.

---

### Post by The Hogg on 2008-04-05
> **billgoldberg said:**
> Yes, it's a dual boot thing.

You should disconnect the hardware correctly in windows, or ubuntu can't mount it.

No dual booting at all :( wish i was because i would have tried that right off! 

had this on another partition (on that 2nd hard drive) and the command it gave in the error works and i can now mount that with no problems!

---

### Post by vanadium on 2008-04-05
If yo do not have windows available, I would try using ntfsfix to scan and repair the drive. Anyway, if you do not anymore use or have Windows, you should consider reformattng your drive in ext3.

---

### Post by twright on 2008-04-05
try sudo mkdir /media/disk first and then use the mount command

---

