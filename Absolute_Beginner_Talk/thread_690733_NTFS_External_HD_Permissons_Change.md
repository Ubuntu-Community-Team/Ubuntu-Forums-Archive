---
title: "NTFS External HD Permissons Change?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by theragingking on 2008-02-07
Is there a way to have more than just root have acess to my NTFS formatted external USB drive? I've found nothing that really helps so far, and was wondering if I could get a n00btastic explanation for this.

The most promising thing I've found so far reads thus:

"With much help from another forum, I got a command code to change the umask for my external HHD. So I can unmount the drive, then remount it with this command line, changing the umask to 022, which works great."

Unfortunately, neither the command line or mentioned forum were posted.

Help please?

---

### Post by wiseguyxp on 2008-02-07
> Disregard <

---

### Post by Rocket2DMn on 2008-02-07
NTFS does not have the same permissions that ext3 does, so chown-ing will not work.    Do you have an entry in fstab for the drive?  Please post the output of
```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by wiseguyxp on 2008-02-07
Bleh, forgot about that.  I never use NTFS and should've thought about that.

---

