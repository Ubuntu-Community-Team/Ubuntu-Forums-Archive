---
title: "File System suggestion (Performance) for large files"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by trini0 on 2008-03-17
I'm redesigning my iscsi server storage subsystem.
Its currently using IET, and its using the whole disk (device) as a LUN.
What I want to do, is change to using files as LUNs.
But my concern is the underlying filesystem that will store these files.
I've read that the best filesystem to hold large (50+ GB) files would probably be JFS or XFS
What filesystem do you suggest that I use to format the disks that would give the best performance?
The server is on a UPS.
Thanks

---

### Post by articpenguin on 2008-03-17
Id say xfs and jfs are the same with large files. But i would pick jfs since it survives a lot better than xfs on a crash.

---

### Post by Widodh on 2008-03-25
Why don't u use LVM on the devices? That is much faster than large files. And it could save you diskusage

---

### Post by insane_alien on 2008-03-25
> **Widodh said:**
> Why don't u use LVM on the devices? That is much faster than large files. And it could save you diskusage

LVM is a partitioning thing. it would still need a filesystem layer on top of this. i recommend XFS but JFS would be good too.

---

### Post by articpenguin on 2008-03-28
> **Widodh said:**
> Why don't u use LVM on the devices? That is much faster than large files. And it could save you diskusage

Yeah faster with large files. But it still wont slove ext3s slow file deletion on large files.

---

### Post by reeseslover531 on 2008-03-28
also isn't reiser pretty good with large files?

---

### Post by Trail on 2008-03-28
I prefer xfs for my large-file storage partitions.

---

### Post by kerry_s on 2008-03-28
+1 jfs with elevator=deadline

i even use jfs on my old slow rig, with elevator=noop, so it can keep up with the slow hardware.

---

