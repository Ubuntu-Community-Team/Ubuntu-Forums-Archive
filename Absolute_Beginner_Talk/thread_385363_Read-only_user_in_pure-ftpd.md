---
title: "Read-only user in pure-ftpd"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by boga on 2007-03-15
Hi,
Is there any way to create a read-only non-anonymous user in pure-ftpd without using file system's access rights (since the file system where the directory to be shared is situated doesn't support access rights)? Or (even better) mount a branch of that file system into the user's home directory as read-only (mount --bind doesn't work since it ignores its options and binds with options used to mount the file system).
Thanks in advance.

---

### Post by boga on 2007-03-19
Thanks to everyone for a lot of help. Just in case someone has the same problem the solution was:
mount -t unionfs -o dirs=/rodir=rw:/soucedir=ro none /targetdir
where /rodir is an empty directory the user doesn't have right to write, /sourcedir is the original directory with writeable data that shouldn't be written, /targetdir is the directory where /sourcedir will appear as read-only.

---

