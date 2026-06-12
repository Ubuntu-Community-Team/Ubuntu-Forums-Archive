---
title: "how to access harddrive under windows [Resolved]"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by doubleuicked on 2007-04-29
i have a partitioned NTFS harddrive that i can access files under ubuntu, however im having trouble copying files onto that harddrive. It says i have no permission to access it.

any suggestions?

cheers

---

### Post by [S|G] on 2007-04-29
You need to install ntfs-3g in order to write files to an NTFS disk.
```
sudo apt-get install ntfs-3g
```
After that unmount your harddrive (replace hdax with your drive):
```
sudo umount -l /dev/hdax
```
And then mount it again using the ntfs-3g driver:
```
sudo mount -t ntfs-3g /dev/hdax /media/mountpoing
```

You can also change your /etc//fstab to use ntfs-3g by default

---

### Post by piti118 on 2007-04-29
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions)
This might help

---

### Post by doubleuicked on 2007-04-30
thanks guys!

---

