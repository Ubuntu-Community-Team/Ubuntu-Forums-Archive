---
title: "Ubuntu 6.10 vs 6.06"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by KMilburn on 2007-02-01
My problem is trying to mount the cdrom using a data cd recording I made on Windows.
Inserting the cd into two cdroms results in nothing happening.
A dvd or music cd works correctly.  I have found commercial cd's do work.

My main question is why does it work on my old system using Ubuntu 6.06?

Using the terminal command MOUNT reports the following:
MOUNT: wrong fs type, bad option, bad superblock on /dev/hdd, missing code page or other error.
In some cases useful info is found in syslog - try dmesg | tail or so.

I tried dmesg | tail and it indicated HDD: media error (bad sector)

On my old system where the cd works, mount reported:
/dev/hdc on /media/cdrom0 type 9660 (ro, noexec, nosuid, nodev, user=ken)

Is there something I am doing wrong in the my burning of the cd's (protocols perhaps)?
Or what am I missing in my new system?

Thank you for your insights into my problem.

Ken

---

### Post by KMilburn on 2007-02-01
This problem is totally my problem.

I have finished checking 20 cds and while one drive on the old machine reads the titles, most of the files are corrupt.

The burning of these cds was 5 years ago.  Poor quality disks perhaps.

Suggest viewers check their old burnings.

Sorry I took your time.

Ken

---

