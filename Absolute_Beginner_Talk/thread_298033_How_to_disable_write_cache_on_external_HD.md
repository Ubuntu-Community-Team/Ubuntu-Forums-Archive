---
title: "How to disable write cache on external HD?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Zar on 2006-11-12
> **outofsync said:**
> Hi,

I'd like to work with files that are in an external USB hard disk. It's not a matter of using it as backup media, but for actually working with the drive (editing files, compiling, etc...).

I'm a bit worried about the write-cache, in case of power failure.

I'd like to be confident that when I save a file, it's actually saved.

If it was just for backups, I could unmount the drive after the backup, but that's not the case.

I am in similar situation as outofsync is.  I searched this forum but couldn't find an answer.  Currently I am doing an awkward workaround - after some work I just eject the HD making sure all the data is written down and then mount it again. 

Is there a simple solution to this issue? If not is there any command by which I can flush out the cache periodically, without ejecting the HD?

Thank you.

---

### Post by Average Joe on 2006-11-12
Try:
> sudo hdparm -W0 /dev/hda
assuming that hda is the hard drive of interest.

---

### Post by Zar on 2006-11-12
> **Average Joe said:**
> Try:

assuming that hda is the hard drive of interest.

Thank you.  But, users not having admin privileges will not be able to use it.  

Can I use the sync command instead?  man sync says it flushes files system buffers, force changed blocks to disk.  Using sync command seems to work, but, I may be doing something wrong.

A launcher with sync command can be created and added to panel. 

Can sync command be used in these situations or will it break anything? :-k

---

### Post by Average Joe on 2006-11-12
Hmm. You could change your /etc/hdparm.conf file such that write-cache is disabled for that drive by default. Then it doesn't require user intervention anymore.

I honestly don't know anything about the sync command, so I am afraid I cannot help you with that.

Or maybe you can change your /etc/fstab file to disable write-cache for that drive.

---

