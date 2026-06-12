---
title: "Stupid beginner question"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by b00mer on 2007-03-06
OK, I have Ubuntu Desktop installed along with Apache2, MySQL 5.0, PHP5.  What do I have to do to be able to write new files in the www directory var/www/?  When ever I try to do this, it comes back with can not write error.  How do I change that?  

Is there a good Apache tutorial for us novices that exists?

---

### Post by dstew on 2007-03-06
Do you have permission to write in that folder?

---

### Post by Brunellus on 2007-03-06
> **b00mer said:**
> OK, I have Ubuntu Desktop installed along with Apache2, MySQL 5.0, PHP5.  What do I have to do to be able to write new files in the www directory var/www/?  When ever I try to do this, it comes back with can not write error.  How do I change that?  

Is there a good Apache tutorial for us novices that exists?
non-privieleged users do not have permission to write anywhere except in their home directories.  You'd need to use sudo. For help with permissions, see [here](http://help.ubuntu.com/community/RootSudo)

---

