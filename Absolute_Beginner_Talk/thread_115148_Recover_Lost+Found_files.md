---
title: "Recover Lost+Found files"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by jhamer9 on 2006-01-10
I had an earlier thread where i had problems with starting kde and even x.  I was getting an error that libz.so.1 file could not be found.  X would not load and i would be presented with a login prompt at a non-gui screen.

After exaustive searching i was just about to give up when i noticed i had new mail in /var/mail/*username*  it stated the following:

```
/etc/cron.daily/standard:
Files were found in lost+found directories.  This is probably the result
of a crash or bad shutdown, or possibly of a disk problem.
These files may contain important information. You should examine them, and
move them out of lost+found or delete them if they are not important.
#1027866
#1027867
...
```

how do i view the files and restore them if needed?  I have a feeling one of the files is the libz.so.1 file i am missing.

fwiw, this is the third time i've had file system problems.  if i get this restored, i think i'll reinstall the OS on a new HDD.

---

### Post by cwaldbieser on 2006-01-10
[QUOTE=jhamer9]I had an earlier thread where i had problems with starting kde and even x.  I was getting an error that libz.so.1 file could not be found.  X would not load and i would be presented with a login prompt at a non-gui screen.

After exaustive searching i was just about to give up when i noticed i had new mail in /var/mail/*username*  it stated the following:

```
/etc/cron.daily/standard:
Files were found in lost+found directories.  This is probably the result
of a crash or bad shutdown, or possibly of a disk problem.
These files may contain important information. You should examine them, and
move them out of lost+found or delete them if they are not important.
#1027866
#1027867
...
```

how do i view the files and restore them if needed?  I have a feeling one of the files is the libz.so.1 file i am missing.

fwiw, this is the third time i've had file system problems.  if i get this restored, i think i'll reinstall the OS on a new HDD.[/QUOTE]

I think you just look in /lost+found.

---

### Post by jhamer9 on 2006-01-10
that's kind of what i thought at first, but i wasn't sure if the files in that directory were compressed or changed to sequential numbers after they were sent there.  For instance all of the files in /lost+found were as follows:

#1027866
#1027867
#1027868
#1027869
#1027870
#1027871
#1027872
#1027873

the thinking was they would be actual files of significance, which they may be, i just don't know what that significance is... :confused:

---

### Post by jhamer9 on 2006-01-10
Well it looks like i might just be screwed and have to re-install the OS.  Although I hate giving up and would really like to try and fix this problem.

If anyone wants some info on the /lost+found directory, this is a pretty good explanation:

[http://howtos.linux.com/guides/Linux-Filesystem-Hierarchy/lostfound.shtml](http://howtos.linux.com/guides/Linux-Filesystem-Hierarchy/lostfound.shtml)

the last thing i'm going to try is install the libz.so.1 file and try to restart X again.

---

