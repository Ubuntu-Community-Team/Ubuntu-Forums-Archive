---
title: "can't repair hfs+ - invalid node structure"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by oysterpog on 2007-10-04
gday all,

firstly i'm new to linux so advance apologies if this is a newb question.

i'm running feisty fawn on a 1.6ghz HP lappy with a gig of ram. i have a HFS+ 400GB SATA drive from my old mac. mounting and reading/writing this drive is fine until it happens to be unbooted uncleanly then it would mount in read-only mode. i fixed this by repairing it with hfs.fsck so that's all good.

now it's stopped mounting entirely and gives an error:

```
zarvox@zoltron:~$ sudo mount /dev/sdb3 -t hfsplus -o rw /media/ze
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sdb3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


 running fsck.hfs on it gives the following errors:

```
zarvox@zoltron:~$ fsck /media/ze
fsck 1.40-WIP (14-Nov-2006)
** /dev/sdb3
** Checking HFS Plus volume.
   Invalid node structure
(3, 0)
   Invalid B-tree node size
(3, 0)
   Invalid record count
(3, 0)
   Invalid B-tree node size
(3, 0)
** Volume check failed.
```

does anyone know what the eff is going on here? if there's any extra info i can post that would help please let me know.

many thanks,

jonas

---

### Post by Sef on 2007-10-04
Read [MacOSHints1]("http://www.macosxhints.com/article.php?story=20070204134513557") and [MacOSHints2]("http://forums.macosxhints.com/showthread.php?t=50723").

---

### Post by oysterpog on 2007-10-04
> **Sef said:**
> Read [MacOSHints1]("http://www.macosxhints.com/article.php?story=20070204134513557") and [MacOSHints2]("http://forums.macosxhints.com/showthread.php?t=50723").

The first article just details how to back up system (on a mac) files before reformatting the main drive. in that case, the guy is able to mount his drive, i am not able to mount my drive. also the applications they are suggesting are OSX; i'm running ubuntu.

the second article suggests reformatting also, which obviously is something i'm trying to avoid.

basically i'd just like to know if this problem is reparable. or at least if it's possible to mount so i can backup and reformat.

---

### Post by oysterpog on 2007-10-04
don't really know what this means but it could be helpful?

```
zarvox@zoltron:~$ dmesg | tail
[ 5575.156000] sdb: Write Protect is off
[ 5575.156000] sdb: Mode Sense: 00 38 00 00
[ 5575.156000] sdb: assuming drive cache: write through
[ 5575.156000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 5575.176000] sd 3:0:0:0: Attached scsi disk sdb
[ 5575.176000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 5652.036000] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 5652.036000] hfs: failed to load extents file
[ 5771.180000] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 5771.180000] hfs: failed to load extents file

```

---

