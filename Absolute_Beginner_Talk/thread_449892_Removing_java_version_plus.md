---
title: "Removing java version plus"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by mfrauenstein on 2007-05-20
Hi All,

Yes I am new. I have loaded 7.03 and Automatix2 on a Ferrari 4000. This is an AMD 64bit processor. I am having problems loading a jre and Mozilla plug-ins as not all jre versions support the AMD64 processor. 

I would like to delete all the other directories that have accumulated on my desktop. Which command do I use? Currently I am switching to "root" via the su command then deleteing the files with rm and then removing the dir with rmdir.

Is there anyway of removing the parent directory and all files and directories below in 1 command?

---

### Post by taurus on 2007-05-20
```
rm -rf **directory**
```
But be real careful with that command because if you put in the wrong directory, bye-bye data...

---

