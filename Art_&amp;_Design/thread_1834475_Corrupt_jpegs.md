---
title: "Corrupt jpegs"
date: 2011-08-27
forum: Art &amp; Design
---

### Post by ants280 on 2011-08-27
Hello, all

The other day I noticed that most of my pictures are corrupt.  They mostly are all jpegs (.jpg) and are "messed up."  It looks as if only a few bits are corrupt, which causes the rest of the photo from a certain point to only contain certain colours, or be grey.  Attached are some examples of the corrupt jpegs (scaled for upload).

The photos that are grey from a certain point in the picture can't be loaded by gimp.

The first thing I did when I noticed these problems was to restore from my backup.  My deja-dup and Back In Time backups wouldn't restore for some reason.  The pictures in my manual backup (folder copy) were also corrupt.  It seems as this problem only happened with my pictures, as my documents and music seem to be intact.

**I want to get my pictures back, if possible (duh).  Does anyone know of some software which may help me accomplish this?  Should I post my problem at a different site?**

I hope this in the right section of the forums.  If it isn't, or could be in a better place, please let me know.

---

### Post by LMP900 on 2011-08-27
I searched the web and the best I could find are paid apps on Windows. In another forum, someone suggested changing the file extension to other common types (e.g. .png, .gif, .bmp), but I don't really know if that will accomplish anything.

Just make sure you keep the originals. You never know when you'll run across a tool to solve your problem.

---

### Post by ofnuts on 2011-08-28
> **ants280 said:**
> Hello, all

The other day I noticed that most of my pictures are corrupt.  They mostly are all jpegs (.jpg) and are "messed up."  It looks as if only a few bits are corrupt, which causes the rest of the photo from a certain point to only contain certain colours, or be grey.  Attached are some examples of the corrupt jpegs (scaled for upload).

The photos that are grey from a certain point in the picture can't be loaded by gimp.

The first thing I did when I noticed these problems was to restore from my backup.  My deja-dup and Back In Time backups wouldn't restore for some reason.  The pictures in my manual backup (folder copy) were also corrupt.  It seems as this problem only happened with my pictures, as my documents and music seem to be intact.

**I want to get my pictures back, if possible (duh).  Does anyone know of some software which may help me accomplish this?  Should I post my problem at a different site?**

I hope this in the right section of the forums.  If it isn't, or could be in a better place, please let me know.Usually it's more than a few bits. More like a complete 4K block. The pics are grey because they lost the chroma data. There is very little you can do to fix these IMHO. 

Anyway I don't think you should worry too much about your Jpegs, because files don't get corrupt like this by chance. Your hard disk is dying or its file system is very heavily messed up, causing new files to overwrite sectors in your JPEGs. Make a thoroutgh backup of all your files, check that it is OK (ie, try to open some of the files in the backup...) and run all the filesystem and hardware checks (SMART data in the HDD) you can lay your hands on against the disk.

Finally, consider that you had 3 backups, and none of them worked... you should also worry about this.

---

