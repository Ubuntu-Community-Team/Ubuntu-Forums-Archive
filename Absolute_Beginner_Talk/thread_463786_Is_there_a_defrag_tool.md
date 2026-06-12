---
title: "Is there a defrag tool?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-04
New to Ubuntu exuse my ignorance.

---

### Post by forestpixie on 2007-06-04
No ther's not - it's not needed!

Loads of info regarding this on the forum

:)

---

### Post by pappapump on 2007-06-04
Linux has no fragmentation issues, it's just perfect.
No virus or malware problems either, so far anyway.

---

### Post by kerry_s on 2007-06-04
Yes, there is, it will kick in automaticaly after a certain amount of boots. It's fsck.

---

### Post by jiminycricket on 2007-06-04
There's one written by jdong called pyfragtools.  Or you can use XFS if you're running mythtv.

---

### Post by vanadium on 2007-06-04
fsck is a tool that checks the consistency of the file system (the chkdsk of GNU/Linux). Defragmentation is not (badly) needed on Linux because by design, the ext3 file system does not quickly fragments the files. Only on rather full disks will large files start to get fragmented.

In GNU/Linux, files will be placed all over the disk right from the start. Thus, the average seek times will be similar on a freshly installed system as on a system that has been used for a long time (and accumulated applications, files, etc...).

A freshly installed Windows system boots relatively fast and, once booted, exhibits very good good performance, because all files are (mostly) contiguously located at the beginning of the disk. Everybody who has used Windows has experienced that that performance quickly deteriorates with time and use, and defragmentation but alleviates the issue temporarily. In Linux, initial performance is not as top notch, but it remains consistent except when the disk gets very full.

---

### Post by revertex on 2007-06-14
take a look here [http://www.novell.com/coolsolutions/qna/15032.html](http://www.novell.com/coolsolutions/qna/15032.html)

---

### Post by freesitebuilder on 2007-06-14
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/) has explanation of why Linux doesn't need defrag (plus other useful info)

---

