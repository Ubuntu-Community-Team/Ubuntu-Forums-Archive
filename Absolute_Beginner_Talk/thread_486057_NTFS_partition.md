---
title: "NTFS partition"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Geir102 on 2007-06-27
I this is probably a normal question. But cant find any good help. I have a NTFS partition that is locatet by ubuntu. But I cant write to it only read, is it possible to fix this?

---

### Post by reckless2k2 on 2007-06-27
yes, query ntfs-3g and that'll give you all you need to setup the read/write of the ntfs partition.

---

### Post by Geir102 on 2007-06-27
OK I'm new to this. So i download this program how do i sett it up?

---

### Post by Nekiruhs on 2007-06-27
Press Alt + F2 and type ntfs-config

---

### Post by Geir102 on 2007-06-27
it tells my that the file dosent exsist

---

### Post by stchman on 2007-06-27
> **Geir102 said:**
> I this is probably a normal question. But cant find any good help. I have a NTFS partition that is locatet by ubuntu. But I cant write to it only read, is it possible to fix this?

ntfs-3g is the package that will allow read/write to NTFS partitions.  Read my tutorial to mount them.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by Inxsible on 2007-06-27
Applications --> Add /Remove. Search for ntfs
 
Install ntfs Configuration Tool. After installation,
 
Applications-->System Tools --> NTFS Configuration Tool. enable write access to internal and external drives.
 
Thats it. You are done.

---

### Post by Geir102 on 2007-06-27
it  works now thanks alott:-D

---

