---
title: "how to mount a partition permanently?"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by candide on 2006-03-05
I want to mount my windowsXP NTFS partition permanently, so it always shows up on my desktop on bootup of my ubuntu. 
Are there some console codes i can type to do this?
Is there some reason i should not do this?

\\:D/

---

### Post by John.Michael.Kane on 2006-03-05
[http://bisqwit.iki.fi/story/howto/ntfs/](http://bisqwit.iki.fi/story/howto/ntfs/)

---

### Post by cotcot on 2006-03-05
This can be done by adding a line in /etc/fstab according to :

[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

It does not give write support to the ntfs partition.

---

