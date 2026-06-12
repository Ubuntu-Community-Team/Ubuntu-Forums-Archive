---
title: "Is ther a journaled file system that both Linux/OSX can use?"
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by second.exodous on 2008-11-02
I was wondering if there was a file system that is Journaled that both Linux/OSX can read/write to.  I'm sick of using Fat32.  I'm getting a external 1TB drive, it's ordered, and was wondering what to format it as.  I use OSX and Linux, so if Windows can't read/write it it's ok.

It seems HFS+ can be read/write in both systems, but Linux can't write unless it's unjournaled.  Ext3 can be, but OSX can't use it in journaled mode.

All the posts I'm reading are pretty old, any one have any current knowledge?

How about Ext4?  Is that read/write under both and journaled under both?

Thanx,
Stan

---

### Post by cyberdork33 on 2008-11-02
It's still all the same.

NTFS is an option though.

---

### Post by WaeV on 2008-11-02
It's ironic how the only journaled FS both Linux and OSX can write to is a Windows FS, but yes, that would be the way to go.

---

### Post by second.exodous on 2008-11-02
Well, I hope things advance with Ext4.  Oh well, NTFS it is.  I guess windows people won't complain if they need to use my drive now.

Thanx

---

### Post by cyberdork33 on 2008-11-02
Hopefully ZFS will be our savior once we can get decent support for it in Linux.

---

