---
title: "what is like NTFS compression for ubuntu?"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-10-23
One thing I like about XP is "file and folder encryption" and "NTFS compression" [not to be confused with compressed (zipped) folders] Is there a similar feature for ubuntu?

In my XP machines I have an NTFS compressed folder within "My Documents" called "Downloads" I download everything to that folder. Besides the obvious advantage of more free disk space, install .exes take up less space on my hard drive, and I use this location to store the .exes until I feel they are worth backing up to CD.

[Oh yea, please don't ramble about NTFS. I know all about it.]

---

### Post by droppedd on 2007-10-23
You probably want some sort of compressed filesystem partition mounted - check out compFused. [http://parallel.vub.ac.be/~johan/compFUSEd/](http://parallel.vub.ac.be/~johan/compFUSEd/)

[INDENT]"This is a compressed overlay filesystem for Linux that supports both transparent READ and WRITE operations. In other words it provides transparent compression of your files while storing them on an existing filesystem Since there are no other compressing filesystems right now for Linux I wrote this thing. Thanks to FUSE and using compFUSEd you can add compression to your existing filesystem in under 5 minutes. No need to reformat!"[/INDENT]

Anyways, most install .exes are already highly compressed... have you checked to see if those actually save you any space when sticking them in an ntfs compressed folder?

Seriously consider whether you need the overhead of automatic compression - you may find that the files that take up the most space are already compressed to the point you won't really save much space using a compressed partition (particularly, MP3s, DivX/XVid/, OGG, JPEGs, etc. are already very compressed and don't benefit much from further compression).

---

### Post by ant2ne on 2007-10-23
> **droppedd said:**
> You probably want some sort of compressed filesystem partition mounted - check out compFused. [http://parallel.vub.ac.be/~johan/compFUSEd/](http://parallel.vub.ac.be/~johan/compFUSEd/)Thanks just what I'm looking for.

> **droppedd said:**
> Anyways, most install .exes are already highly compressed... have you checked to see if those actually save you any space when sticking them in an ntfs compressed folder?

Seriously consider whether you need the overhead of automatic compression - you may find that the files that take up the most space are already compressed to the point you won't really save much space using a compressed partition (particularly, MP3s, DivX/XVid/, OGG, JPEGs, etc. are already very compressed and don't benefit much from further compression).](*,)
   =;

---

