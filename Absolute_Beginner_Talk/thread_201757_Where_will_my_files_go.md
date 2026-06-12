---
title: "Where will my files go?"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Lord Landis on 2006-06-22
I've been using Ubuntu on my laptop for several weeks, and I just finished installing it on my desktop last night.  I need to restore several gigabytes of data, and I'm not sure where it will go.

See, the desktop has two hard-drives.  HDA has '/' as its mount point, and HDB has '/home' as its mount point.  If I copy everything from the backup discs to '/home', will they all end up on the second drive, or what?

Also, is there any way to view the two drives independently?  Whenever I view the filesystem, it just gives me a full directory, and I have no idea which specific drive I'm actually looking at.

Thanks in advance.

---

### Post by bruce89 on 2006-06-22
[QUOTE=Lord Landis]See, the desktop has two hard-drives.  HDA has '/' as its mount point, and HDB has '/home' as its mount point.  If I copy everything from the backup discs to '/home', will they all end up on the second drive, or what?[/QUOTE]
Files put in /home will end up on the second drive, as this is where /home is mounted.
[QUOTE=Lord Landis]Also, is there any way to view the two drives independently?  Whenever I view the filesystem, it just gives me a full directory, and I have no idea which specific drive I'm actually looking at.[/QUOTE]
There is real point in viewing each drive seperatly, Linux has a filesystem, and each drive is mounted on a specific part, so your /dev/hdb is mounted at /home, and everything else is on /dev/hda.  See [http://en.wikipedia.org/wiki/Root_directory](http://en.wikipedia.org/wiki/Root_directory), and [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard).

---

### Post by Lord Landis on 2006-06-22
bruce89,

Thank you!  You've been most helpful.  I think that I understand the filesystem a little better now.

---

