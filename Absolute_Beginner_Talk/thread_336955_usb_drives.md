---
title: "usb drives"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-12
ASSUME:  (yeah I know)  200gig usb drive........

To make it available as a storage place for any and all users with no restrictions and just one partition.

What should the format be.  ext3?  /?   

Is and can this all be accomplished in gpart


Thanks

---

### Post by meng on 2007-01-12
ext3, fat, ntfs, reiserfs are all filesystems.
/ is a mountpoint, not a filesystem.

My advice is: ext3 is fine if it is only ever going to be physically connected to a Linux box. If you may want to connect it to a Windows box, go with fat32 instead. If Windows machines need to access the drive REMOTELY, then it doesn't matter, ext3 is fine.

---

### Post by squrl on 2007-01-12
I was avoiding fat32 because of the size limitations. I might want to park a part image file there and it wouldn't be large enough and would have to be split into several partitions.

---

### Post by meng on 2007-01-12
Then use ext3. A Windows machine would need fs-driver to read it by direct USB connection, but would be okay to read it through samba if it were mounted on a Linux box.

---

### Post by squrl on 2007-01-12
How do you change ownership and permissions on a usb drive?

---

