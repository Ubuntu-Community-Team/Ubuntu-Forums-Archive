---
title: "Temporarily Mount NTFS Drive Read-Only"
date: 2013-06-01
forum: Any Other OS
---

### Post by Iggy64 on 2013-06-01
I am running Bodhi Linux, currently built on Ubuntu Precise.  I would like to mount a USB drive that is formatted NTFS.  I would like the drive to be write protected (i.e., read-only).

I have disabled the automount options in my file managers, PCManFM and Fileman (the default Bodhi FM), since they automatically mount things read-write.

I do not want to modify /etc/fstab, since I will only mount this drive occasionally.  I would simply like to use the mount command to mount the drive read-only.

When I attach the drive, it gets the following device ID: /dev/sdb1
I created the mount point /media/Music
My user ID is 1000

I have tried a variety of mount commands, including:

> sudo mount -t ntfs-3g -o ro /dev/sdb1 /media/Music

and, later,

> sudo mount -t ntfs-3g -o uid=1000,gid=1000,umask=0377 /dev/sdb1 /media/Music

The drive mounts OK, but it continues to be read-write, rather than read-only, as shown here:

> ls -l /dev/sdb1
brw-rw---- 1 root disk 8, 17 Jun  1 17:59 /dev/sdb1

I have messed with this for many hours, and am getting nowhere.

Can someone suggest the proper code for mounting this drive read-only?

Am I using the proper method to test how the permissions are currently set?  (i.e., does the ls -l command show the correct permissions for an ntfs drive?)  I don't want to test by trying to write to the drive, unless I absolutely have to.

Thanks, in advance.

---

### Post by howefield on 2013-06-01
Thread moved to the "*Other OS/Distro Support*" forum.

---

