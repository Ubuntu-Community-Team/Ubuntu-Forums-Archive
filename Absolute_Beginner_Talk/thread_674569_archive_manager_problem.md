---
title: "archive manager problem"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by .Ix on 2008-01-21
archive manager can't extract any tar files. :( i can see what's inside them, but i'm not allowed to extract.


this is what i get when i try extracting one:

tar: cfgPeopsSoft: Cannot utime: Operation not permitted
tar: gpuPeopsSoftX.cfg: Cannot utime: Operation not permitted
tar: libgpuPeopsSoftX.so.1.0.17: Cannot utime: Operation not permitted
tar: peops_soft_readme_1_17.txt: Cannot utime: Operation not permitted
tar: peops_soft_version_1_17.txt: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors

---

### Post by Tenken on 2008-01-21
You could try untarring it from the command line with:

```
tar -xvvf  foo.tar
```

---

### Post by .Ix on 2008-01-21
still get the same problem :(

drwxr-xr-x fafner/fafner     0 2008-01-09 08:01 hdldumb-1.5a-i386/
-rwxr-xr-x fafner/fafner  1640 2008-01-09 07:45 hdldumb-1.5a-i386/setup.pl
tar: hdldumb-1.5a-i386/setup.pl: Cannot utime: Operation not permitted
-rwx------ fafner/fafner 39611 2008-01-09 07:44 hdldumb-1.5a-i386/hdldumb
tar: hdldumb-1.5a-i386/hdldumb: Cannot utime: Operation not permitted
-rw------- fafner/fafner  1585 2008-01-09 07:47 hdldumb-1.5a-i386/changelog
tar: hdldumb-1.5a-i386/changelog: Cannot utime: Operation not permitted
-rw------- fafner/fafner   303 2008-01-01 00:59 hdldumb-1.5a-i386/readme
tar: hdldumb-1.5a-i386/readme: Cannot utime: Operation not permitted
-rw-r--r-- fafner/fafner   388 2008-01-01 01:13 hdldumb-1.5a-i386/hdldumb.desktop
tar: hdldumb-1.5a-i386/hdldumb.desktop: Cannot utime: Operation not permitted
-rwx------ fafner/fafner 56485 2007-12-29 06:32 hdldumb-1.5a-i386/hdldumb.glade
tar: hdldumb-1.5a-i386/hdldumb.glade: Cannot utime: Operation not permitted
-rwxr-xr-x fafner/fafner 276544 2008-01-09 08:01 hdldumb-1.5a-i386/hdl_dump
tar: hdldumb-1.5a-i386/hdl_dump: Cannot utime: Operation not permitted
drwx------ fafner/fafner      0 2008-01-09 07:44 hdldumb-1.5a-i386/pix/
-rwx------ fafner/fafner   4673 2007-12-29 03:28 hdldumb-1.5a-i386/pix/DVD.xpm
tar: hdldumb-1.5a-i386/pix/DVD.xpm: Cannot utime: Operation not permitted
-rwx------ fafner/fafner   9896 2007-12-29 03:43 hdldumb-1.5a-i386/pix/icon.xpm
tar: hdldumb-1.5a-i386/pix/icon.xpm: Cannot utime: Operation not permitted
-rwx------ fafner/fafner    456 2007-12-29 03:30 hdldumb-1.5a-i386/pix/DVDDL.xpm
tar: hdldumb-1.5a-i386/pix/DVDDL.xpm: Cannot utime: Operation not permitted
-rwx------ fafner/fafner    453 2007-12-29 03:27 hdldumb-1.5a-i386/pix/CD.xpm
tar: hdldumb-1.5a-i386/pix/CD.xpm: Cannot utime: Operation not permitted
tar: hdldumb-1.5a-i386/pix: Cannot utime: Operation not permitted
tar: hdldumb-1.5a-i386: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors

---

### Post by Tenken on 2008-01-21
Are you trying to extract the file to a seperate directory? If so make sure your have permission to write to it.

```
sudo tar -xvvf foo.tar
```

---

### Post by .Ix on 2008-01-21
lol there we go, thanks. i should have had permission to write, it's just a random folder on my drive. oh well, it's ok now.

---

### Post by PeterJS on 2008-01-21
> **.Ix said:**
> lol there we go, thanks. i should have had permission to write, it's just a random folder on my drive. oh well, it's ok now.

There are very few "random" folders in the linux file system. Generally writing directly to system files isn't recommended, and as an install method it's terrible because it overwrites things rather indiscriminately and doesn't write the proper meta-data for the package manager.

---

