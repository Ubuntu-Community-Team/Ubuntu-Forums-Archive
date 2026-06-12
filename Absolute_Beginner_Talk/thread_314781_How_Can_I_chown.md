---
title: "How Can I chown?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-08
Just installed Edgy.  Have a dual boot system with Win on hda and Edgy on hdb.

How can I give myself ownership of files on an NTFS partition?  I installed ntfs-3g and can write to these partitions but apparently can't chown.  But even on FAT partitions chown doesn't seem to work.  The terminal will say the owner was changed but when I check it's still root.  One more:  all the directories/files in the NTFS partitions I've checked list the associated group as "plugdev."  By using "adduser" in a terminal I found out I'm a member of that group.  But the group isn't listed in System > Administration > Users and Groups.  ?????
How can I get a list of all the groups of which I'm a member?

Thanks,
Buck

---

### Post by Bachstelze on 2006-12-08
FAT32 cannot handle file permissions and Linux cannot handle file permissions on NTFS. To define owner, group and chmod, use the uid, gid and umask parameter in your mount command or in your fstab.

---

### Post by Adramelech on 2006-12-08
As said, set permision on fstab but remember to use option default_permissions, it was the only way i get permission to work.

Here is an example from my fstab:

```
UUID=045CC12D5CC119F6 /media/hda2     ntfs-3g    defaults,gid=ntfs-3g,umask=007,default_permissions,locale=en_US.utf8 0 0
```

---

### Post by Buck2348 on 2006-12-08
Thank you both very much for your replies.  I read in the ntfs-3g guide that sharing was a problem in ntfs--thought maybe there was a workaround, which you've given me.  I didn't know about the problem with FAT32.  I'll get to work on my fstab.  :-D

---

