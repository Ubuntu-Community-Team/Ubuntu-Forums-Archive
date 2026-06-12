---
title: "DVD-ROM/DVD-RW DMA question..."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-08-09
I have two drives, a dvd-rom and a dvd-rw.  In my /dev directory I have cdrom, cdrw, dvd, and dvdrw.  Should i have to enable DMA for all of them? Or just cdrom and cdrw or dvd and dvdrw?

---

### Post by arjun.shankar on 2006-08-10
Try this:

**ls -l /dev/cdr***

out of cdrw and cdrom, one will be a link.

**ls -l /dev/dv***

again, one will be a link.

---

### Post by memos on 2006-08-10
And how to enable both?

---

### Post by arjun.shankar on 2006-08-10
do this:

**hdparm -v /dev/devicename**

If you see
**using_dma    =  1 (on)**

Then you are already good to go.

Otherwise do this:

**sudo hdparm -d /dev/devicename**

then again:
**hdparm -v /dev/devicename**

just to check!

---

### Post by memos on 2006-08-10
Ok i fixed.Thanks man.

---

### Post by echo $USER on 2006-08-10
Thanks, turned out DMA was enabled out of the box, atleast for me and my v. of dapper.

---

### Post by arjun.shankar on 2006-08-11
Same for me. Seems to be enabled in all distros nowadays.

---

