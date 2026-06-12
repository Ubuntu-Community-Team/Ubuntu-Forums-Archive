---
title: "1gb file takes 10 seconds, 3gb takes over an hour?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by guice on 2007-05-22
Does this make sense?

I'm trying to copy over data from my XP drive to Ubuntu. The 1.2gb file copied over in 10 seconds but when I tried to copy over the 3.6gb file, it takes over an hour?!

Why is that? What's going on here? This is from an NTFS, SATA drive to Ubuntu ext2, IDE drive.

I just copied over a different 4.4. gig file and it copied over under 2 minutes. Why is this one file taking over an hour?? Could it be due to fragmentation?

---

### Post by ronocdh on 2007-05-23
> **guice said:**
> Does this make sense?

I'm trying to copy over data from my XP drive to Ubuntu. The 1.2gb file copied over in 10 seconds but when I tried to copy over the 3.6gb file, it takes over an hour?!

Why is that? What's going on here? This is from an NTFS, SATA drive to Ubuntu ext2, IDE drive.

I just copied over a different 4.4. gig file and it copied over under 2 minutes. Why is this one file taking over an hour?? Could it be due to fragmentation?
My first thought was indeed fragmentation. NTFS isn't as bad as FAT32, but it does still fragment much moreso than ext3 (which I believe rarely fragments until the drive is at least 80% full). I would try defragmenting in Windows. Also, do you have ample (10-15%) free space on both drives?

---

### Post by szaka on 2007-05-23
> **guice said:**
> Does this make sense?

It perfectly makes sense if you're still using an obsolete version of ntfs-3g. Version 1.328 and laters fixed and improved significantly the performance of large file copyies. Here are the ntfs-3g release history and benchmark numbers with early and new ntfs-3g releases:

[http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)
[http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/124](http://article.gmane.org/gmane.comp.file-systems.ntfs-3g.devel/124)

Type 'sudo ntfs-3g' to see your ntfs-3g version.

---

