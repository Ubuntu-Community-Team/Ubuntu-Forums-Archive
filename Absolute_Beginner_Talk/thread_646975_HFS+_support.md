---
title: "HFS+ support"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-12-21
I have an external hard drive with an HFS+ format and I cant see any of its contents with ubuntu. Can anyone help me with this.

---

### Post by stburman on 2008-01-03
I don't have the means to test this, but I hope these instructions will work.  First you'll want the hfsplus package.  ```
$sudo aptitude install hfsplus
```
Then you should be able mount it like any filesystem.```
$sudo mount -t hfsplus [device path] [directory path]
```  Of course, replace [device path] with the real device path (something like /dev/hdb1) and [directory path] with the real directory path where you want to mount it.  
Sorry I can't assure you that this will work.  If anyone is more knowledgeable please correct me.  I hope this helps.

---

