---
title: "Write to NTFS problems"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by PropheticAngel on 2007-09-07
I'm using ntfs-3g to try and get write access to my 500 gig, NTFS external.  It worked perfectly for a long time, but about two weeks ago, I got a box telling me to run ntfsfix.  After that was done, it told me to force the drive, so I added:
```
/dev/sdb1 /media/drive ntfs-3g defaults,force 0 0
```
to the /etc/fstab

But now, when I try to write to the drive, for example create a folder, I get a box saying:
**Error Creating New Folder**
Error "I/O error" creating new folder.

How can I get my external working perfectly again w/ write access?

---

### Post by dca on 2007-09-07
Before you do anything can the drive still be recognized by plugging it into a WinXP box???  You know, auto-recognized and folders being added/deleted?

---

### Post by dwhitney67 on 2007-09-07
I'm curious as to why the OP and others need to insert an entry into /etc/fstab to mount their NTFS drives?  I do not have an entry in my file-system table and my drive mounts just fine, and it's mounted read-write.

All I did was follow these [instructions]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html").

---

### Post by asmoore82 on 2007-09-07
you may want to check the drive for physical failure with **badblocks** ...

```
~$ sudo badblocks /dev/sdb1
```
(no output is good; if numbers are output, there are bad blocks)

Even before that, It would probably be a great idea to boot up windoze and check for filesystem errors.

---

### Post by PropheticAngel on 2007-09-07
It seems to work fine in windows XP...I'm checking for badblocks now

---

### Post by stchman on 2007-09-07
> **PropheticAngel said:**
> I'm using ntfs-3g to try and get write access to my 500 gig, NTFS external.  It worked perfectly for a long time, but about two weeks ago, I got a box telling me to run ntfsfix.  After that was done, it told me to force the drive, so I added:
```
/dev/sdb1 /media/drive ntfs-3g defaults,force 0 0
```
to the /etc/fstab

But now, when I try to write to the drive, for example create a folder, I get a box saying:
**Error Creating New Folder**
Error "I/O error" creating new folder.

How can I get my external working perfectly again w/ write access?

For external media I recommend FAT32 as it can be read and write by nearly any OS.  The only thing is that FAT32 has a 4G file size limitation.

---

### Post by szaka on 2007-09-07
> **PropheticAngel said:**
> 
Error "I/O error" creating new folder.

I bet your ntfs-3g release is too old. Such type of inconsistent NTFS volumes are  supported since ntfs-3g 1.616. The latest release is 1.826. Just upgrade and your problem should go away.

---

### Post by Nythain on 2007-09-07
if you do have an fstab entry, dont you have to assign a umask, and possibly uid and gid for ntfs... that way its mounted with with the right owner/group/and permissions??? all i see in your entry is defaults wich works great to cover the default options but doesnt do much for permissions, try adding umask=0000,uid=1000,gid=1000 and rebooting, or just remounting will work, and see if that helps any at all???

---

### Post by PropheticAngel on 2007-09-08
No badblocks.
Added lines to fstab, no better.
Updated ntfs-3g to the newest version, nothing.

---

### Post by szaka on 2007-09-08
Please send the output of 
```

egrep -i 'dma|ntfs' /var/log/daemon.log

```

---

### Post by PropheticAngel on 2007-09-08
There was no output to that.

---

### Post by szaka on 2007-09-08
Then try
```

egrep -i 'dma|ntfs' /var/log/daemon.log*

```
The ntfs-3g output must be in a file under the /var/log directory.

---

### Post by PropheticAngel on 2007-09-08
```

/var/log/daemon.log.0:Sep  7 15:06:34 rat-laptop ntfs-3g[4245]: Error reading $Mft record(s)
/var/log/daemon.log.0:Sep  7 15:06:34 rat-laptop ntfs-3g[4245]: Unmounting /dev/sdb1 (BOB'S DRIVE) 
/var/log/daemon.log.0:Sep  7 15:34:08 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:08 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:12 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:12 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:13 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:13 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:13 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:13 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:13 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:13 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:13 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:13 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:14 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:22 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:22 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:34:26 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:34:26 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:39:32 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:39:32 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:40:43 rat-laptop ntfs-3g[4266]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 15:40:43 rat-laptop ntfs-3g[4266]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 15:49:15 rat-laptop ntfs-3g[4266]: Skipping unrepresentable filename (inode 1957)
/var/log/daemon.log.0:Sep  7 15:49:15 rat-laptop ntfs-3g[4266]: Skipping unrepresentable filename (inode 5888)
/var/log/daemon.log.0:Sep  7 20:58:01 rat-laptop ntfs-3g[4237]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 20:58:01 rat-laptop ntfs-3g[4237]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 20:58:04 rat-laptop ntfs-3g[4237]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 20:58:04 rat-laptop ntfs-3g[4237]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  7 20:58:07 rat-laptop ntfs-3g[4237]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  7 20:58:07 rat-laptop ntfs-3g[4237]: Could not allocate new MFT record
/var/log/daemon.log.0:Sep  8 00:06:24 rat-laptop ntfs-3g[10519]: Version 1.328 
/var/log/daemon.log.0:Sep  8 00:06:24 rat-laptop ntfs-3g[10519]: Mounted /dev/sdb1 (Read-Write, label "BOB'S DRIVE", NTFS 3.1) 
/var/log/daemon.log.0:Sep  8 00:06:24 rat-laptop ntfs-3g[10519]: Options: noatime,rw,silent,allow_other,nonempty,fsname=/dev/sdb1,blkdev,blksize=4096 
/var/log/daemon.log.0:Sep  8 00:46:24 rat-laptop ntfs-3g[10519]: Mft record 0xa1c6 was marked unused in mft bitmap but is marked used itself.  Corrupt filesystem or library bug!  Run chkdsk immediately! 
/var/log/daemon.log.0:Sep  8 00:46:24 rat-laptop ntfs-3g[10519]: Could not allocate new MFT record
Binary file /var/log/daemon.log.5.gz matches

```

---

### Post by szaka on 2007-09-08
You're still using the old driver, not the new one. Remove all and install only the latest one.

---

### Post by PropheticAngel on 2007-09-08
It said 1.8* until I re-installed the NTFS configuration tool using apt-get.

---

