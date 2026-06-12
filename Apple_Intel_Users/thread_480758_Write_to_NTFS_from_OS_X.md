---
title: "Write to NTFS from OS X"
date: 2007-06-21
forum: Apple Intel Users
---

### Post by ronocdh on 2007-06-21
I came across this link on Lifehacker and thought it might be useful to the triple booters here. I personally use ext3 on all my externals, as I can use installable filesystems to get them to work in [OS X]("http://sourceforge.net/projects/ext2fsx/") and [WinXP]("http://www.fs-driver.org/"), but NTFS read/write might be cool for certain circumstances. [Here's the link]("http://www.hackszine.com/blog/archive/2007/06/howto_readwrite_to_ntfs_drives.html?CMP=OTC-7G2N43923558").

---

### Post by ivesjd on 2007-06-21
A good guide, although I thought I remembered reading about something to do this that didn't use fink. But maybe not.

---

### Post by ~joe~ on 2007-06-23
> **ivesjd said:**
> A good guide, although I thought I remembered reading about something to do this that didn't use fink. But maybe not.
Yes, you can use a binary driver for MacFUSE that doesn't require any compilation.
[http://www.lifehack.org/articles/lifehack/how-to-read-and-write-ntfs-windows-partition-on-mac-os-x.html](http://www.lifehack.org/articles/lifehack/how-to-read-and-write-ntfs-windows-partition-on-mac-os-x.html)

One thing to keep in mind, however, is that NTFS write support is still a bit buggy, and I wouldn't use it on a regular basis if any important files were on that partition.

---

