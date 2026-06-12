---
title: "manually mount floppy with unknown fs"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by dmizer on 2006-08-30
okay i actually just accidentally landed on the correct fs type with a lucky guess.  but i'd ultimately like to figure out how to manually mount a floppy with an unknown file-system type.

providing i know the file system type (in this case ext2), i know i can mount with:
```
sudo mount -t ext2 /dev/fd0 /media/floppy
```
or, i think i might be able to add a mount line in fstab like so:
```
/dev/fd0     /media/floppy     auto     noauto,user     0     0
```
followed by sudo mount -a (which i suppose might be easiest).

but i'd like to know one of the two following:
1) is it possible to determine a floppy's file system before mounting?
2) is there a way to manually mount a floppy such that it will auto-detect the file system?

---

### Post by Jussi Kukkonen on 2006-08-30
From *man mount*: 
> If  no -t option is given, or if the auto type is specified, mount will try to guess the desired type.  If mount was compiled with the  blkid  library, the  guessing  is  done by this library. Otherwise, mount guesses itself by probing the superblock; if that does not turn up anything that looks familiar, mount will try to read the file /etc/filesystems, or, if that does not exist, /proc/filesystems.  All of the filesystem types listed there will be tried,  except for those that are labeled "nodev" (e.g., devpts, proc, nfs, and nfs4).

*blkid* is also a program that you can use to detect filesystems.

---

### Post by anaconda on 2006-08-30
sudo mount -t auto /dev/fd0 /media/floppy

actually if you omit the "-t auto" it just might work also..

---

### Post by dmizer on 2006-09-01
> **anaconda said:**
> sudo mount -t auto /dev/fd0 /media/floppy

actually if you omit the "-t auto" it just might work also..

yeah ... tried that.  got a syntax error for undefined file system then.

it's just puzzling to me because this is a native linux format, but it won't auto detect the file system.

edit:
you know ... i'm a complete dumbass.  ssh was my problem.  i didn't realize that the terminal i was using to mount the floppy was ssh'd into a remote box.

kina difficult to mount a local floppy on a remote machine.

btw sudo mount -t auto ... worked fine once i had a terminal open for the right box. :(

---

