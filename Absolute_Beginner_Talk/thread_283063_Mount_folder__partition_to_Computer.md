---
title: "Mount folder / partition to Computer"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by shepherdnick on 2006-10-23
Hey there,

Just wondering if it is possible to mount a partition at startup so that it shows up in Computer.  I have already edited fstab so that it mounts to /media/osshare but I also want it to appear in Computer as either a folder or a hard drive.

Thanks in advance.

---

### Post by Marsolin on 2006-10-23
Since you are already mounting the drive in one location I would create a symlink in Computer to point to it.

---

