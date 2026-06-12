---
title: "NTFS disk lost a folder"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by shadowdance on 2007-08-29
Hi,

I mounted a NTFS folder in fstab, and when i tried to sudo mount -a, it said something about "FUSE - disk is busy" or something like that. I restarted, and it worked fine.

A folder was suddenly missing, though. It was the folder I had accessed to test my changes. This is really terrible. It is completely gone, and I can find none of the files through search. What has happened???

---

### Post by chuckyp on 2007-08-30
NTFS write support is still buggy.  Thats why everyone warns about using it.

---

### Post by dwhitney67 on 2007-08-30
I do not understand the following:  You stated that you mounted the NTFS drive _and then_ you ran "mount -a".  Why?  A little overkill isn't it?  The "mount -a" mounts everything (possible) that is listed in your /etc/fstab file.  If you have an entry in your /etc/fstab file for the NTFS drive it is not necessary.  Follow these [instructions]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html") on how to setup your NTFS drive.

A device can appear (and actually is) busy if you are currently browsing a folder or a file on that device.  Trying to unmount it while it is busy will generally generate an error.  Heed the error warning and get out of the folder (or file) before attempting to unmount.  Do not ignore the message and just yank the USB cable out.

---

