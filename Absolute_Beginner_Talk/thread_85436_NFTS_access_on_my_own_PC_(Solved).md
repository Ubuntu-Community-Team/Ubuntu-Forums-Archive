---
title: "NFTS access on my own PC (Solved)"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by valnar on 2005-11-02
I have XP on my laptop and had Ubuntu 5.04.  Worked great, for the little I played with it.

I now wiped Hoary and put on 5.10 instead.  It found my NTFS volumes and created icons for them.  I don't have permissions to these volumes though.  My single user that I created during installation is not root of course.

So in my inifinite newbieness, how do I fix this?  What the file that I edit to allow my user (me) to have read-access to my NTFS volumes on the same PC?

Robert

---

### Post by LHZ on 2005-11-02
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

should help you out.

---

### Post by pete on 2005-11-02
[QUOTE=valnar]I have XP on my laptop and had Ubuntu 5.04.  Worked great, for the little I played with it.

I now wiped Hoary and put on 5.10 instead.  It found my NTFS volumes and created icons for them.  I don't have permissions to these volumes though.  My single user that I created during installation is not root of course.

So in my inifinite newbieness, how do I fix this?  What the file that I edit to allow my user (me) to have read-access to my NTFS volumes on the same PC?

Robert[/QUOTE]

You need to add the following line to the end of /etc/fstab:

/dev/[name_of_ntfs_partion]       [path_to_mountpoint]  ntfs    nls=utf8,umask=0222 0       0

For example, my NTFS partition is hdb5, and my mount point is /mnt/ntfs, so I have the following in my fstab file:

/dev/hdb5       /mnt/ntfs     ntfs    umask=0222       0       0

---

### Post by valnar on 2005-11-02
I found it in the page.  Thanks!

---

