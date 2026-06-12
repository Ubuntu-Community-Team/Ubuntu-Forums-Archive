---
title: "Can't resize a partition (even though using live CD)"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by alarichall on 2007-10-21
I have my operating system (Ubuntu 6.06) installed on a partition (/dev/hda3) which is now too small, so I've been trying to resize it using the software which comes with the Ubuntu 6.06 live CD. The partitions are all unmounted, and I've got a big unallocated space available.

But here's what the screen looks like when I right-click on /dev/hda3 and try to resize it:

[IMG]http://alarichall.googlepages.com/Screenshot2.png[/IMG]

It says that the maximum size for the partition is 3004 MB, and won't let me make it any bigger. Can anyone help me fix this problem? It's getting hard to use my computer, because there's not enough space on /dev/hda3 :-(

Thanks!

---

### Post by Pumalite on 2007-10-21
You need to use Gparted Live CD:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Boot from it and resize.(it will not mount your drive/partition)

---

### Post by alarichall on 2007-10-21
Thanks, I'll try that when I have a blank CD-R then.

---

