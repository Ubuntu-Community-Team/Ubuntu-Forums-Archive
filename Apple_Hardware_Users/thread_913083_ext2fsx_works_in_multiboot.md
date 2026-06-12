---
title: "ext2fsx works in multiboot?"
date: 2008-09-07
forum: Apple Hardware Users
---

### Post by PaulFXH on 2008-09-07
I'm using OS X on a MB C2D with a number of Linux OSes (including Ubuntu).
I have installed [ext2fsx]("http://bmannconsulting.com/macosx/how-to/ext2-for-mac/ext2fsx-readme") in OS X and it seems to work more or less.
So, my two Ubuntu partitions (/ and /home) automount and I can read them without problem from OS X.
However, none of the other partitions automount for reasons unknown, despite all of them being formatted to the same ext3 as the Ubuntu volumes.
Of the ext3 partitions that don't automount, I can mount them with this command
```
sudo mount -t ext2 /dev/disk0s3 /Volumes/foresight
```
(it only works when I specify ext2 as the fs; ext3 doesn't work and gives me this error
```
mount: exec /usr/sbin/mount_ext3 for /Volumes/foresight: No such file or directory
```)
However, what's strange is that, whereas before mounting I can cd into /Volumes/foresight, once I've mounted the volume, when I try to cd into this directory I get
> -bash: cd: foresight: No such file or directory
If I unmount the partition, then the /Volume/foresight directory becomes accessible from the command line once again.
After mounting from the command line, the mounted directory shows up in the list System Preferences>>ExtFSManager.
However, if I try to mount a volume from ExtFSManager, I get this error:
> Command: Mount
Device: disk0s5
Message: Unknown Error (The filesystem may need repair. Please use Disk Utility to check the filesystem.)
Error: 0xC047

Has anybody been able to do better with accessing ext3 volumes in OS X using ext2fsx?

---

