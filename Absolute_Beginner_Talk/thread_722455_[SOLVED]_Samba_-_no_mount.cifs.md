---
title: "[SOLVED] Samba - no mount.cifs?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by DamonChyld on 2008-03-12
I am trying to get my NAS drives user/pass out of my etc/fstab file and am following dmizer's thread here  -- [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

I have ran into a wall when trying to mount the drive, I do not have a mount.cifs file in my sbin! Google searching it told me to install smbclient; it was installed but I reinstalled anyway but still no love. Any idea what I am doing wrong?

The samba packages I have installed are:
```
libsmbclient
samba
samba-common
smbclient
```

dmesg | tail
```
 [  414.218961]  CIFS VFS: cifs_mount failed w/return code = -22
[  526.485376]  CIFS VFS: No username specified
[  526.485384]  CIFS VFS: cifs_mount failed w/return code = -22
[ 1094.122650] cdrom: This disc doesn't have any tracks I recognize!
[ 1340.155299]  CIFS VFS: No username specified
[ 1340.155307]  CIFS VFS: cifs_mount failed w/return code = -22
[ 1591.392287]  CIFS VFS: No username specified
[ 1591.392296]  CIFS VFS: cifs_mount failed w/return code = -22
[ 1769.805801]  CIFS VFS: No username specified
[ 1769.805809]  CIFS VFS: cifs_mount failed w/return code = -22

```

man mount.cifs
```
No manual entry for mount.cifs

```

---

### Post by glennric on 2008-03-12
You need to install the packages smbfs.

---

