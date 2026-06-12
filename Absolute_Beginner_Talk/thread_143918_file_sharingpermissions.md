---
title: "file sharing/permissions"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-03-13
I've got few directories on my NTFS drive I'd like to share with some users on my
system, but not the whole drive contents.

What's the easiest way to achieve this?

---

### Post by LordBug on 2006-03-13
If it's just a few directories, I'd suggest copying them off onto your Ubuntu partition(s) and setting permissions appropriately.

---

### Post by mlind on 2006-03-13
[QUOTE=LordBug]If it's just a few directories, I'd suggest copying them off onto your Ubuntu partition(s) and setting permissions appropriately.[/QUOTE]

that's not possible I'm afraid. Data must remain on windows drive :(

---

### Post by aysiu on 2006-03-13
Can you explain a bit more about your situation? For example why the data must be on Windows or why only certain folders should be available?

I don't want you to get too personal, but if you explain the exact situation, someone may be able to think of an alternative solution.

---

### Post by mlind on 2006-03-13
no problem. 

basically some of the data on the drive is sensitive, so access needs to be
restricted. If I could somehow mount only certain folder instead of whole drive.

I got close to the solution by symlinking folders I want to allow access.

Can I define mount point for harddrive which is only accessible for root, 
say /media/D, which points to NTFS drive D:

but allow access through symlink, /mnt/project/, which will allow access to
D:\web\project

?

---

### Post by aysiu on 2006-03-13
The problem is really that NTFS doesn't support *Linux* permissions.

So these are your viable options:

1. Encrypt the data that's sensitive--this is probably a good idea in general--and mount the entire NTFS partition as read-only for everyone.

2. Store the sensitive stuff on Ubuntu and use [http://www.fs-driver.org/](http://www.fs-driver.org/) to allow people from Windows (who should have that privilege) to view those sensitive documents. I'm not sure how that works permissions-wise, though.

Ultimately, I think encryption may be the only way to go. Anyone who has physical access to your machine can usually look at any file, even if she doesn't officially have "permission." She can simply boot into recovery mode, and she's root. Or she can load up a live CD and mount your Windows or Ubuntu drive and see all the files.

Unless the data is encrypted, it doesn't matter what permissions you set. If someone wants to see those files, she can.

---

