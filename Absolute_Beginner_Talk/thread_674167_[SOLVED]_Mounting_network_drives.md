---
title: "[SOLVED] Mounting network drives"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2008-01-21
Hi all,

I have 2 partitions that I wish to mount, each with different permissions

/dev/sdg1 will mount to /media/Drop and be fully writable, but not executable, to all users who can login to my server

/dev/sdg2 will mount to /media/Backup and be read only, can be executable if needed to list files and what not, and can once again be accessed by anyone who is logged into my server.

Also, I want to own these drives, I do not want root to own them

What should my fstab look like?

-kt

---

### Post by dstew on 2008-01-21
What format do the partitions have? This is important when assigning permissions.

---

### Post by kernel tom on 2008-01-21
right now the writable partition is ext3
and the read only partition is vfat

should i change these?

---

### Post by dstew on 2008-01-21
No need to change the partition formats. Here are my first guess for fstab entries:```
/dev/sdg1 /media/Drop ext3 rw,noauto,user,noexec 0 1
/dev/sdg2 /media/Backup vfat ro,noauto,user,exec 0 1
```I am not so sure about the vfat line. I think you will be owner if you are owner of the mount points.

---

### Post by kernel tom on 2008-01-21
If the permissions for the mount folder are rwxrwxrwx, and the partition is mounted as noexec, will a user be able to execute a file?

---

### Post by dstew on 2008-01-21
I don't know. I think not, but you could just do the experiment to see.

---

