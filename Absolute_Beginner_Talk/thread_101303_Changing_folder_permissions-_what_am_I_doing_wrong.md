---
title: "Changing folder permissions:- what am I doing wrong?"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by Vulpus on 2005-12-09
Can anyone explain why when I try to do this:

*dt@viglen:~$ sudo chown dt /media/windows*

I get this:

[I]chown: changing ownership of `/media/windows': Operation not permitted
dt@viglen:~$[/I]

---

### Post by Sheco on 2005-12-09
if it is an NTFS file system, it is read only

---

### Post by Vulpus on 2005-12-09
No, it is a FAT32 partition

---

### Post by Sheco on 2005-12-09
you can't assign ownership on windows filesystems anyway.

as far as I know, youre trying something like chown dt C: (C: doesnt have linux like ownership)

anybody correct me if I'm wrong.

Your solution is editing /etc/fstab, there you can configure who owns the mount point.

---

### Post by deNoobius on 2005-12-09
Yup, I tried to do the same thing and ran into the exact same issue. [This thread]("http://www.ubuntuforums.org/showthread.php?t=92288") has the solution.

---

### Post by aysiu on 2005-12-09
You may find this link helpful as well:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by Vulpus on 2005-12-09
[QUOTE=deNoobius]Yup, I tried to do the same thing and ran into the exact same issue. [This thread]("http://www.ubuntuforums.org/showthread.php?t=92288") has the solution.[/QUOTE]

Thank you for that.  Problem sorted.  

Though I do have a nagging doubt that the relevant line in my fstab USED to be set up like that before I upgraded to Breezy?  Then again I might be imagining it.

---

