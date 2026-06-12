---
title: "Partition Permissions"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Johnny p on 2007-08-04
hello, I have my hard drive partitioned into 3 partitions, One being for windows, one being for Ubuntu, and one I use for important files,( no OS installed ) labeled "New Volume" . Ubuntu will allow me to access the files, just not add or remove any from New Volume. Is there a way i can make that partition fully accessible by Ubuntu?

---

### Post by taurus on 2007-08-04
What filesystem is that "New Volume"?

```
sudo fdisk -l
cat /etc/fstab
```

If it's ext3, you can just change the ownership.  But if it's ntfs, then you need to install ntfs-3g before you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Johnny p on 2007-08-04
Woooooo, thank you so much, that link did it.

---

### Post by McTek on 2007-08-04
I have a fat32 partition, how do I change ownership on it. I now have to enter a password access it.
PS: Also would like to have it auto mount.

See URL :

[http://ubuntuguide.org/wiki/Ubuntu_d...o_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_d...o_read.2Fwrite)

---

