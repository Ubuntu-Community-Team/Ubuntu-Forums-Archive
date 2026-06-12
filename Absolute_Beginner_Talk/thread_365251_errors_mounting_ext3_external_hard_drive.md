---
title: "errors mounting ext3 external hard drive"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Kulgan on 2007-02-19
Hi all :D

I bought a nice new external hard drive a little wile ago, which was formatted to fat32. I reformatted the entire thing to ext3, as I wanted to use symlinks and unix permissions. The whole thing worked fine for weeks- mounting on it's own and such was perfect, until I randomly start getting this evil error when trying to mount it:

> 
mount: wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or other error In some cases, useful info is found in syslog - try dmesg | tail or so.


That bit about the bad superblock doesn't sound good at all, to me... 
So I do dmesg | tail:

> 
SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
sda: Write Protect is off
sda: Mode Sense: 10 00 00 00
sda: assuming drive cache: write through
 sda: sda1 < sda5 >
sd 0:0:0:0: Attached scsi disk sda
JBD: no valid journal superblock found
EXT3-fs: error loading journal.
JBD: no valid journal superblock found
EXT3-fs: error loading journal.


Error loading journal, eh? I presume that would be because I forgot to unmount it before pulling out the plug some time?

Well, I can't mount it, and there are some files on there that I would really rather like to save - it was my backup disk as well as AMP server... Who would have thought the backup would go as I was reformatting :mad: 

Are there any programs anyone has to reccommend concerning recovery?

Thanks,
Kulgan

---

### Post by taurus on 2007-02-19
Try to fsck it.

```
sudo fsck /dev/sda5
```
or
```
man fsck
```
for more info.

---

### Post by Kulgan on 2007-02-19
Wow, quick reply!

Ran it, as you said, though it was only in /sbin, not the normal executable dirs. Same thing... 

> # /sbin/fsck /dev/sda5
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Superblock doesn't have has_journal flag, but has ext3 journal inode.
Clear<y>? yes

DATA was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Journal inode is not in use, but contains data.  Clear<y>? no

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
/lost+found not found.  Create<y>? yes

Pass 4: Checking reference counts
Pass 5: Checking group summary information

DATA: ***** FILE SYSTEM WAS MODIFIED *****

DATA: ********** WARNING: Filesystem still has errors **********

DATA: 10932/30539776 files (0.8% non-contiguous), 11753754/61048992 blocks


It still has errors, eh? So just to check, run it again... 
> # /sbin/fsck /dev/hda5
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
fsck.ext2: No such file or directory while trying to open /dev/hda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Hmm... :confused:

---

### Post by taurus on 2007-02-19
Try to mount it as ext2 instead of ext3!

---

### Post by Kulgan on 2007-02-19
hehehe, rebooted because of updates and it worked fine :D I suppose that since it is now ext2, forgetting to unmount is not as severe a mistake?

Cheers,
Kulgan

---

### Post by taurus on 2007-02-19
You still need to unmount it before you unplug it or some files could get damaged.  Always unmount in Linux/Unix.

---

### Post by Kulgan on 2007-02-19
of course :D

I was just though that it was the journaling that was the most vulnerable to that kind of thing... Not important from any POV. 

Thanks a ton for your quick replies :D

-K

---

