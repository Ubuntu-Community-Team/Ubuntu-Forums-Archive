---
title: "format partition help"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by DestroyMicroshaft on 2007-12-18
Is there a way for me to format a partition to hfs+ from ubuntu, I mean anyway even 3rd party software?

---

### Post by dward526 on 2007-12-18
fdisk is a command line option, use 'man fdisk' for instructions.  You can also add gparted from synaptic and use a partition magic like interface

---

### Post by DestroyMicroshaft on 2007-12-18
ive tried gparted wont let me format to hfs+, only vfat's ntfs, and linux fs's like ext3, etc.

---

### Post by Keith Hedger on 2007-12-18
fdisk does'nt support hfs, try hfsutils and hfsplus in the repos, i dont have them installed so i can't check if they will actually format a hfs drive
see this:[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

### Post by dward526 on 2007-12-18
> **DestroyMicroshaft said:**
> ive tried gparted wont let me format to hfs+, only vfat's ntfs, and linux fs's like ext3, etc.

```
 sudo apt-get install hfsutils 
```

Now gparted should have hfs support

---

