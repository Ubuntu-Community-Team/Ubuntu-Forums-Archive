---
title: "recovering deleted files"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by cf1709 on 2007-04-01
this relative of mine formatted my windows pc and installed linux on it without asking my permission. the problem is that backing up those files of mine is still not complete. is there any way to recover those precious lost files?

---

### Post by dstew on 2007-04-01
What operating system is working, is it Windows or Linux? If Linux, you can see if your Windows partition(s) are still there by using the command **sudo fdisk -l** on the command line. The command line is in the Terminal application.

---

### Post by annda on 2007-04-01
do not use the formatted disk. preferably, get the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") on another computer and boot from it on the affected machine.

---

### Post by cf1709 on 2007-04-01
he wiped ALL/ANYTHING in that drive, removed the windows partitions, and made a new partition with clean linux install in it. is there still hope in it?

---

### Post by 23meg on 2007-04-01
Yes; if he didn't overwrite the partition entirely with a new filesystem, it may be rescued. If he did, you may have a chance to recover certain files with a raw recovery program such as [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

### Post by cf1709 on 2007-04-01
edit: he removed the windows partitions and made a new filesystem on the whole hard drive... i've seen testdisk... is it feasible to use? if so, how?

---

### Post by 23meg on 2007-04-01
If a new filesystem overwrote the old one, you have little or no chance with Testdisk.

---

### Post by cf1709 on 2007-04-01
no hope already? is there no other way to recover that lost partition? i'm getting deperate... and getting ready to kill somebody...

---

### Post by 23meg on 2007-04-01
Give it a try; you won't lose anything. Also try the following: gpart, parted (type "rescue", "%0" for start, "%100" for end), foremost, and as a last resort, Photorec.

---

### Post by cf1709 on 2007-04-01
i've used photorec and it recovers no files. however, when using testdisk, i've analysed and found some fat32 lba partition and when i pressed "p" (to view the list of files), it has listed nothing and said that "No file found, filesystem seems damaged"

---

### Post by 23meg on 2007-04-01
Try the "search deeper" option and see if it finds anything else.

---

