---
title: "difference between /mnt and /media folder"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-12-20
What's the difference between the folders /mnt and /media?
When mounting partitions they tend to go to /media if you follow other ppls instructions.  But when using programs like Truecrypt where you mount encrypted partition-files it's help file instructs you to mount at /mnt.

I've mounted stuff all over / (root) by accident before but to me it seems like /mnt and /media folders serve the same purpose or don't they?

---

### Post by annda on 2006-12-20
all other (older) Linux distributions i worked with mounted drives to /mnt. ubuntu's (and debian's???) default is /media. it's just a matter of convention.

---

### Post by hal10000 on 2006-12-20
According to Linux File Hierarchy Standard ([http://www.pathname.com/fhs/pub/fhs-2.3.html]("http://www.pathname.com/fhs/pub/fhs-2.3.html"))
/media is intended to be for removable media (like usb sticks, cdrom, floppy)
and /mnt is used for Mount points for a temporarily mounted filesystem (like partitions fron a harddrive, network shares etc.)
But some distributors use one of them as mount points for all media.

---

### Post by bodhi.zazen on 2006-12-20
What hal10000 said :p

Also devices/partitions mounted in /media will show on the desktop as /mnt generally will not.

---

