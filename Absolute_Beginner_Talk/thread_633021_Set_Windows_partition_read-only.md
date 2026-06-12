---
title: "Set Windows partition read-only"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by afritzse on 2007-12-06
Hi there

I installed ubuntu 7.10 alongside XP. It runs fine, I just feel somewhat uncomfortable allowing read-write access to the Windows partition.

In order to mount the Windows partition as read-only, is it fine to just add "ro" to the /etc/fstab options?

Thanks

Arthur

---

### Post by kpkeerthi on 2007-12-06
[Use ntfs instead of ntfs-3g]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")
This will work for gutsy too.

---

### Post by ByteJuggler on 2007-12-06
Adding "ro" in the fstab should be OK.  Aside, the normal ntfs driver also supports limited NTFS read-write support so whether you use that or NTFS-3G I would suggest you use the "ro" option in either case.

---

