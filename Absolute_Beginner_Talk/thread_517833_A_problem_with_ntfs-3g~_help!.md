---
title: "A problem with ntfs-3g~ help!"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by xellzhang on 2007-08-05
When I ran ./configure of ntfs-3g 1.710, I got a warning at last:
****************************************************************************
* WARNING WARNING WARNING WARNING WARNING WARNING WARNING WARNING *
* FUSE is NOT installed with root directory executable prefix. This means *
* that automounting NTFS volumes during boot could fail. You can configure *
* FUSE to prevent this the below way during its installation: *
* ./configure --exec-prefix=/ *
* WARNING WARNING WARNING WARNING WARNING WARNING WARNING WARNING *
**************************************************************************** 

I just went ahead and I can mount ntfs partition manually. But as the warning said, I failed to mount them during boot.

How can I reconfigure FUSE? thanks

---

### Post by nitro_n2o on 2007-08-05
as the error say you have to ./configure --exec-prefix=/

---

### Post by xellzhang on 2007-08-05
I think FUSE package has been installed as a core right? Does that mean I have to remove the package and compile/install one by myself?

---

### Post by xellzhang on 2007-08-09
Does anyone know about this?
Should I sudo apt-get remove libfuse2 or do something else?

---

