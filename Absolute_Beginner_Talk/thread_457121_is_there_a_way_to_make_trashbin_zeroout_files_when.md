---
title: "is there a way to make trashbin zeroout files when its emptyed?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-05-28
is there a way to make gnomes trashbin securely zero out the trash when its emptyed?

---

### Post by kernel tom on 2007-05-29
if by "securely" you mean that there is no trace of it left on your hard drive I have not come accross anything to use with the trash can

I would say your best bet would be to restore the files, then open a terminal where they are and use the "shred" command

I believe that command has options you may like, look em up:

in terminal
man shred

---

### Post by Nekiruhs on 2007-05-29
Try 
```
shred ~/.Trash/&.*
```

---

### Post by cosmoshell on 2007-06-02
> **Nekiruhs said:**
> Try 
```
shred ~/.Trash/&.*
```

is this going to work 

CAUTION: Note that shred relies on a very important assumption:
that the file system overwrites data in place.  This is the traditional
way to do things, but many modern file system designs do not satisfy this
assumption.  The following are examples of file systems on which shred is
not effective, or is not guaranteed to be effective in all file system modes:

* log-structured or journaled file systems, such as those supplied with
  AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

i use ext3

---

