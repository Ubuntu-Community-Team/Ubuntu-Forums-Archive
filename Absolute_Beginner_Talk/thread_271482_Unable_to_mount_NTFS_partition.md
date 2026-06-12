---
title: "Unable to mount NTFS partition"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2006-10-04
Cheers,

I have an NTFS partition and I'm trying to mount it into Ubuntu.  I tried doing the instructions on how to mount ntfs patitions 

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

but when I did
sudo ntfsmount /dev/hda5 /media/stuffs -o umask=0007

I get this error 
Couldn't mount device '/dev/hda5': Operation not supported
Windows did not shut down properly.  Try to mount volume in windows, shut down and try again.
Mount failed.

What do I do now? aside from installing Windows XP again.

---

### Post by divague on 2006-10-04
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

---

