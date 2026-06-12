---
title: "Disable automatic mounting of unneeded partitions"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-04
Ubuntu (Gnome) automatically mounts all partitions at boot time. I think it is better to disable this feature in /etc/fstab and enable only those partitions that you use in Linux.

For example, if you are using Windows and Ubuntu, you could disable the Windows system partition, and others that are used by Windows only. In any case, if you really want them at any time while in Ubuntu, you can mount them manually.

This makes your system more secure in a sense. I have done this and I hope others do it. If you haven't, why not?

---

### Post by Xian on 2006-03-04
[QUOTE=AtinLango]I have done this and I hope others do it. If you haven't, why not?[/QUOTE]

Because not everyone would agree obviously. :)
Maybe people want and/or need their Win partitions already mounted.

Just add the 'noauto' feature to the "options" column.
Then you can still use only your local paths when mounting.

---

### Post by xmastree on 2006-03-04
[QUOTE=AtinLango]Ubuntu (Gnome) automatically mounts all partitions at boot time.[/QUOTE]No it doesn't. :confused: 

I had to edit my fstab to mount my windows and shared partitions automatically.

---

### Post by AtinLango on 2006-03-04
[QUOTE=xmastree]No it doesn't. :confused: 

I had to edit my fstab to mount my windows and shared partitions automatically.[/QUOTE]

Mine automatically mounted and displayed applets for all partitions. Thats why I was not happy having all of them cram the desktop.

Otherwise, it is possible that during installation we specified different parameters so as to cause the difference.

---

### Post by aysiu on 2006-03-04
I don't know why this would make your system more secure. The Windows partitions are mounted with "defaults," meaning that only root can access them. That's why I had to create tutorials like this:

[http://www.psychocats.net/linux/mountwindows](http://www.psychocats.net/linux/mountwindows)

because people actually want to view and/or modify their Windows partitions.

In Hoary, by the way, no partitions were automatically added to your /etc/fstab. I'm hoping for Dapper, it'll be smart enough to make NTFS added as read-only and FAT32 added as read/write, as these are *very* common requests.

---

