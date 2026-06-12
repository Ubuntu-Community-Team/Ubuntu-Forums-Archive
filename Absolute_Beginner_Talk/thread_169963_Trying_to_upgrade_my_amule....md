---
title: "Trying to upgrade my amule..."
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by nir78 on 2006-05-03
I am trying to upgrade my amule from ubuntu standard one to 2.1.1
I downloaded the .deb package from amule forum but when I try to run it I get this message:
```
nir@main-storage:~$ sudo dpkg -i amule_2.1.1-2ubuntu1breezy1_i386.deb
(Reading database ... 109800 files and directories currently installed.)
Preparing to replace amule 2.1.0+CVS20060109-1~ots2 (using amule_2.1.1-2ubuntu1b reezy1_i386.deb) ...
Unpacking replacement amule ...
dpkg: error processing amule_2.1.1-2ubuntu1breezy1_i386.deb (--install):
 trying to overwrite `/usr/share/man/man1/ed2k.1.gz', which is also in package a mule-ed2k
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 amule_2.1.1-2ubuntu1breezy1_i386.deb
nir@main-storage:~$

```

What's the problem ??

Nir

---

### Post by macdo on 2006-05-03
Try uninstalling your old aMule first, and see what that gives you.
I think that you can just copy your Temp and Incoming folders to the new installation, if you've backed them up. You'll find them in /home/yourusername/.aMule, normally.

---

### Post by nir78 on 2006-05-04
Hi,

I uninstalled amule cvs and still... the same exact error!!!!
I tried deleting the file mentioned but nothing!

anybody ??

Nir

---

