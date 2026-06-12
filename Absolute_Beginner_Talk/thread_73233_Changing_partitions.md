---
title: "Changing partitions?"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by RedHerring on 2005-10-08
When I installed Ubuntu I chose the option to have it create it's partitions from free space.  It created one big partition and one swap partition.

I'd like to have another partition to store all of my personal files in so that when I upgrade/reinstall I won't lose all of my stuff.

It's not possible to do that without making the current partitions unreadable, right?

---

### Post by Gustav on 2005-10-09
[QUOTE=RedHerring]When I installed Ubuntu I chose the option to have it create it's partitions from free space.  It created one big partition and one swap partition.

I'd like to have another partition to store all of my personal files in so that when I upgrade/reinstall I won't lose all of my stuff.

It's not possible to do that without making the current partitions unreadable, right?[/QUOTE]
It might be possible, use a live-CD or perhaps partition-magic create the new partition. But make very sure to back up all your data :)

---

### Post by Hobbsee on 2005-10-09
or use gparted.  That should work fine, and is free

Make sure you backup first though!

---

### Post by mlomker on 2005-10-09
> It's not possible to do that without making the current partitions unreadable, right?

I'd recommend backing your things up (as others stated), download a copy of [Knoppix]("http://www.knoppix.net/get.php"), and then run [gparted]("http://gparted.sourceforge.net/screenshots.php") to resize your current partition.

Afterward you'll need to format the new partition and create a statement in /etc/fstab to mount it where you want (perhaps by renaming your /home directory and then creating a new one and mounting the partition there).

It'll require a little work.  ;)

---

