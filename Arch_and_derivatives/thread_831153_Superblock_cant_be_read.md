---
title: "Superblock cant be read"
date: 2008-06-16
forum: Arch and derivatives
---

### Post by SnakeHips on 2008-06-16
Hi ,I've had a search around here but cant find a fix specifically related to "Arch"...

at boot

```

/dev/sda2: clean, ...
/dev/sdb1: clean, ...

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Please repair manually......
```

any ideas how to fix? My boot files are on /dev/sda1 mounted as /boot with an ext2 filesystem

I'm an Arch newbie but can follow instructions ok :-)

---

### Post by Rumor on 2008-06-16
Generally that error tells you to log in as root to manually repair the problem. You should be able to log in as root and then run fsck or e2fsck to try to repair the issue.

You can refer to this thread for more info: [http://bbs.archlinux.org/viewtopic.php?id=35412](http://bbs.archlinux.org/viewtopic.php?id=35412)

---

