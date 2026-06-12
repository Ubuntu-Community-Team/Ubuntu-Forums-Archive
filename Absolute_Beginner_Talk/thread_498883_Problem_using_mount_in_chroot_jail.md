---
title: "Problem using mount in chroot jail"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Tirial on 2007-07-11
I'm quite new to ubuntu, and have gotten most of the things working that I want.  However, I've been fighting with this one for a couple days, and decided to ask some people who know what they are doing.

I have created a chroot jail, with a scponly user.  User can log on correctly, and is locked into the jail and can only run sftp.  

However, I want to mount, inside the jail, a file system that this user can read, but cannot write or execute anything.  The directory I want to be able to view is on a USB mounted volume.  I want all the other users on the system to have read write access to that volume.

so I tried mount -o ro, bind /media/drive /home/scponly/drive

But apparently, when you use the bind option, it ignores the other flags on the command, and thus it mounts the volume as read write inside the jail.

Anyone have a suggestion on how I can fix this?

---

### Post by sab0403 on 2007-07-13
Not so much a suggestion as a confirmation of the problem. According to the man:

> Since Linux 2.4.0 it is possible to remount part of the file  hierarchy
somewhere else. The call is ```
mount --bind olddir newdir
```
After this call the same contents is accessible in two places.  One can also remount a single file (on a single file). This call attaches only (part of) a  single  filesystem,  not  possible submounts.  The entire file hierarchy including submounts is attached a second place using```
mount --rbind olddir newdir
```**Note that the filesystem mount options will remain the same as those on the  original  mount  point,  and  cannot  be changed by passing the -o option along with --bind/--rbind.**

---

