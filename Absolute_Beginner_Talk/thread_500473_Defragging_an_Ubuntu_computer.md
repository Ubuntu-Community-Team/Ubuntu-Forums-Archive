---
title: "Defragging an Ubuntu computer"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Georgeiger on 2007-07-13
Hi, All

How do I go about defragging my Ubuntu computer?  

      Regfards, Georg

---

### Post by bobplano on 2007-07-13
i don't think that ubuntu requires defragging. every so often when it boots up it checks the filesystem to see if everything is ok. it lists the amount of fragmentation, but it doesnt worry about it

---

### Post by macogw on 2007-07-13
You don't. Ext3 might get a liiiittle fragmented (it'll say during fsck like bobplano said) but never more than like 5%.  FAT32 and NTFS are really bad because of the way they write files.  They don't leave enough buffer for modifying files.  Ext3 leaves buffer space so you can make modifications to files without fragmenting them (unless you had only like 3% of drive space left and then modified a small file into a HUGE one....at which point you have bigger problems, like a 97% full hard drive).  

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Nekiruhs on 2007-07-13
Ext3 Filesystem is much more efficient than NTFS. Basically instead of just shoving a file in the first open space and then spilling over into other, fragmented blocks, it looks for a space with ample size and puts it there. Thus reducing fragmentation until the drive gets almost full.

---

### Post by Nythain on 2007-07-13
> **macogw said:**
> but never more than like 5%.
i have a sata drive that averages 11.0% non contiguous... though all my IDE drives never even reach 1%... just thought id throw out there that more than 5% is possible, and has happend to me and my friend (both with SATA drives)

---

