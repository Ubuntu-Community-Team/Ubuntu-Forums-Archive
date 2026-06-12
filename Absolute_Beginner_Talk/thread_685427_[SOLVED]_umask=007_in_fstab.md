---
title: "[SOLVED] umask=007 in fstab"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by kaiju on 2008-02-02
in fstab, i have umask=007 for my fat partition.

could i use any other umask value to keep the same permissions but without files being set executable at mount, while at the same time keeping directories executable so i can browse them?

---

### Post by nick_h on 2008-02-02
You can use *dmask* to set a *umask* for directories and *fmask* to set a *umask* for regular files.

For the manual page type:
```
man mount
```

---

### Post by spiderbatdad on 2008-02-02
my understanding is that mounted file system permissions are defeault (777) -umask. so a umask value 022 would result in permissions set to 755, and so on. So, by default, none should be executable. 6=rw,  7=rwx,  4=r,  2=w, 1=x. The order is user, group, other. so 644 would be user=read/write,  group=read,  other=read. Umask 007, I'm guessing would =0770.

---

### Post by kaiju on 2008-02-03
@ nick_h, this is exactly what i needed. who would've thought to look in man mount? :P
big thanks

@ spiderbatdad, i'm afraid i just can't follow all these numbers. three digit permissions are still ok, and calculating umasks from them sort of works too, but how 007 becomes 0660 really beats me. i wish there was a clear explanation for all this somewhere.

---

### Post by spiderbatdad on 2008-02-03
sorry if that was confusing. Fat file systems do not support unix file permissions. The directory to which you are mounting the file system (in Linux) does have permissions. By default, I believe, these permissions are 777-umask....at any rate....not executable...as a directory wouldn't be. And no, you cannot change umask without affecting the permissions of the directory. But remember the mounted files, in the directory, are not governed by any permissions.

---

### Post by kaiju on 2008-02-03
i know i can't individually set permissions for files on a fat disk. that's why i needed to set the appropriate umask in ftsab, so all the files automatically get the permissions i want them to have, at mount time.
the separate parameters for files and directories mentioned by nick_h let me achieve just that: now i have 'dmask=027,fmask=137' in fstab, with the uid and gid set to my user and group. this way, after mounting the partition, i alone have read/write access and only the members of my group have read access.
the different values for files and directories enabled me to have executable directories and non-executable files, which is just what i needed ;)

---

### Post by Blario on 2008-03-21
I'm having a related problem.  I'm trying to mount an ext3 partiiton to a directory, but I don't have write access to it.  I've tried adding umask to the options in /etc/fstab, but EXT3-fs is telling me that the option is wrong.  Here are a few lines from my file... /dev/sda9 is the one I'm having the problem with.

```

/dev/sda8 /home              ext3    defaults        0       2
/dev/sda9 /home/shared   ext3    auto,umask=000         0       2
/dev/sda7 /opt                  ext3    defaults        0       2

```

---

