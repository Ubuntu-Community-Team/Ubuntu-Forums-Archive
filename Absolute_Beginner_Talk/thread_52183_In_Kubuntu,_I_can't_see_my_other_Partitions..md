---
title: "In Kubuntu, I can't see my other Partitions."
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by HappyPaul on 2005-07-26
Hello:

I have Kubuntu installed on my laptop along with two other Linux distributions and three versions of Windows. When I try to look at any of my other Partitions through media:/, I get the error message, "Could not mount device.   mount: can't find /dev/hdax in /etc/fstab or /etc/mtab".  Any Ideas?

Thanks,

Paul

---

### Post by wrtrdood on 2005-07-27
Check /etc/fstab to see if they're listed.  If not, use *fdisk -l /dev/hda* (assuming of course that you only have one drive) to see the partition table.  You can then use this to add them to the fstab which should then make it accessible to the desktop.

---

