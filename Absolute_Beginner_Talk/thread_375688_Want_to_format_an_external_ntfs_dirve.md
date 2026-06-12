---
title: "Want to format an external ntfs dirve"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-03-04
I have an external ntfs hard drive that I would like to format to allow for me to write to it (I have tried many ways to write to it, and everyone of them never worked). The only thing is that it is readonly so I can't just up and format it.

Any advice?

---

### Post by taurus on 2007-03-04
What filesystem do you want to format it to?  You can actual write to ntfs with ntfs-3g driver now.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by guysmiley25 on 2007-03-04
You can try this to get read/write:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

There are other guides on that page that will help with stuff too.

To format you can just use gparted.

```
sudo aptitude install gparted
```

If you do not already have it.

---

